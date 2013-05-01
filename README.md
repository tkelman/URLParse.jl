A parser to parse URL string representation into components and re-create the URL string back from components. Modeled after the python urlparse library. A URL can be of the form:
````
scheme://netloc/path;parameters?query#fragment
````

URLComponents
-------------
The parsed URL components are stored and returned in an instance of URLComponents. 

Component fields and accessor methods:
*   **scheme**
*   **netloc**
*   **url**
*   **params**
*   **query**
*   **fragment**
*   **username(u::URLComponents)** : Extracts username from the netloc field. Returns a string if present or nothing otherwise.
*   **password(u::URLComponents)** : Extracts password from the netloc field. Returns a string if present or nothing otherwise.
*   **hostname(u::URLComponents)** : Extracts hostname from the netloc field. Returns a string if present or nothing otherwise.
*   **port(u::URLComponents)** : Extracts port from the netloc field. Returns an int if present or nothing otherwise.

There is an internal cache of URLComponents maintained as an optimization for repeated use of same URL string.


APIs
----
<dl>
    <dt>urlparse(url::String)</dt>
    <dd>Parse a URL into 6 components: <scheme>://<netloc>/<path>;<params>?<query>#<fragment>. Returns an instance of URLComponents.</dd>
    <dt>urlunparse(u::URLComponents)</dt>
    <dd>Join back 6 components of the URL back to recreate a URL string.</dd>
    <dt>urldefrag(url::String)</dt>
    <dd>Removes any existing fragment from URL. Returns a tuple of the defragmented URL and the fragment (empty string if none were there).</dd>
</dl>


TODO
----
*   parse\_query\_string: to create a list/dict of name-value pairs
*   urljoin: to overlay a relative url on a base url 
*   is\_valid: validate URL string to be conforming to scheme rules


NOTE
----
In addition to the methods documented above, the following are also exported, in anticipation of being useful elsewhere.
*   **urlsplit** and **urlunsplit**: Similar to urlparse and urlunparse, but ignores the 'parameters' part of the url. That is, assumes URLs of form scheme://netloc/path?query#fragment.
*   **rsearch**: Search in a string from end to beginning. Similar to Base.search, but in the reverse direction.
*   **rsplit**: Split a string with a delimiter starting from the end. Similar to Base.split but in the reverse direction.

