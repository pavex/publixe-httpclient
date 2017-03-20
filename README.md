# publixe-httpclient
Simple XML HTTP Requester for Node.js special for React and React Native applications based on XMLHttpRequest

No long explanation, here are examples:

```js
import {JsonRequest} from 'publixe-httpclient';

var r = new JsonRequest();

r.setUrl('https://raw.githubusercontent.com/pavex/publixe-httpclient/master/samples/sample.json');
r.setContentType('application/json');
r.setMethod('GET');
r.setParams({});

r.onSuccess(() => {
	console.log(r.getStatus());                // Status code
	console.log(r.getResponse());              // Completely response object
	console.log(r.getData());                  // Only contents of root element "data"
});
r.onFailure(() => {
	console.log(r.getStatus());                // Status code
	console.log(r.getLastError());             // Error message generated by requester
	console.log(r.getErrorObject());           // Error object included message and code
});

r.send();
```

## Using in React Native

```js
import {JsonRequest} from 'publixe-httpclient';

// Customize xhr for Chrome debugging
var xhr = GLOBAL.originalXMLHttpRequest	? GLOBAL.originalXMLHttpRequest : XMLHttpRequest;
var r = new JsonRequest(xhr);

r.setUrl('https://raw.githubusercontent.com/pavex/publixe-httpclient/master/samples/sample.json');
r.setContentType('application/json');
r.setMethod('GET');
r.setParams({});

// Add content type in classic way
if (xhr == XMLHttpRequest) {
	r.setHeader('content-type', 'application/json');
}

r.onSuccess(() => {
	console.log(r.getStatus());                // Status code
	console.log(r.getResponse());              // Completely response object
	console.log(r.getData());                  // Only contents of root element "data"
});
r.onFailure(() => {
	console.log(r.getStatus());                // Status code
	console.log(r.getLastError());             // Error message generated by requester
	console.log(r.getErrorObject());           // Error object included message and code
});

r.send();
```


I try to prepare short documentation of this class. 
