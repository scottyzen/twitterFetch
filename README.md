# twitterFeed

Fetches your latest tweets

Show your latest tweet or tweets on your website.

Twitter offers two options to show your twitterfeed on your website:
  
#. [Using a Twitter widget](https://dev.twitter.com/web/overview)
#. [Using the Twitter REST API](https://dev.twitter.com/rest/public)

They are fully supported by Twitter and might be the best solution for you.

Disadvantages are:

#. Limited layout possibilities (widget).
#. Cookies are send to Twitter, which, without warning, might be illegal in your jurisdiction (widget).
#. Page load (widget).
#. Needs server side scripting (api).

TwitterFeed provides a solution without these disadvantages. It fetches the Twitter widget (without sending
cookies) and makes the tweets available in JavaScript, to be placed on a webpage the way you want.
Less than 2kB, twitterFeed is also very lightweight.

## Quickstart

Start by downloading [twitterfeed.js](twitterfeed.js) to you server and including it in your web page.

```html
<script src="twitterfeed.js">
```

In your HTML, make sure you have a place to show the tweets:

```html
<div id="tweets"></div>
```

Now, use twitterFeed to fetch the tweets and show the first one:

```javascript
twitterFeed.fetch('345615146724495360', {}, function (tweets) {
	if (!tweets || tweets.length == 0) {
		return;
	}
	document.getElementById('tweets').innerHTML = tweets[0];
});
```

But don't use the widget id 345615146724495360, that belongs to my [@edwinmdev](https://twitter.com/edwinmdev) Twitter account.
 
## How to make your own widget id?
 
Create a [Twitter widget](https://twitter.com/settings/widgets/new) and look at the generated code.
You'll find data-widget-id="..." with the number you can use.

## API

The twitterFeed fetch function takes three parameters:

```javascript
twitterFeed.fetch(widgetId, options, callbackFunction);
```

### widgetId
The widget id you get when creating a widget, see above.

### options
An object literal with several options:

images (boolean): when false, prevents loading images that are not needed (default: false).

plaintext (boolean): when false, encodes some entities to make the text safe for HTML (default: false).    

hyperlinks (boolean): when true, turns urls and Twitter @usernames into hyperlinks (default: true).
    
Example:
```javascript
{
	images: false,
	plaintext: true
}
```

### callbackFunction
The function that is called back with one argument containing an array with tweets.

## License

TwitterFeed is  copyright 2016 Edwin Martin and MIT licensed.
