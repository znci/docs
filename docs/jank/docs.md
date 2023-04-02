
This page shows how to initialize Jank relatively easily.
# How to Initialize
Place the contents from [this](https://raw.githubusercontent.com/znci/jank/main/jank.js) file into the root directory of your project and name it anything you wish, but it is preferred to be named `jank.js` as that is what the documentation will follow.

You can now use:
```js
const { jank } = require("./jank");
```
in your index file.

## Settings
The settings are extremely easy to set up, with little amounts of fields.
```js
jank.settings({
	PORT: 3193,      // just an example port, follows basic port guidelines
	OPTIONS: [       // all available options
		"body-parser",
		"ejs",
		"public",      // static reading from /public/
		"cors",
		"routes",      // route handling, see Routes
	]
})
```

## Routes
Routes are very easy to set up and initialize, with method and route validators.
Create a directory in your root project, called `routes`. Here you can make subdirectory and the project will pick these up automatically, and add them to the server.
If a route is not used with the valid method, it will send an error message referring to the invalid method used.

An example route file could look like this, in the base routes directory:

```js
module.exports = {
	method: "GET",
	path: "/",      // adds a route to /
	handler: (req, res) => {
		res.send("Hello World!");
	}
}
```

or this, in an example API subdirectory:
```js
module.exports = {
	method: "GET",
	path: "/api/time",      // adds a route to /
	handler: (req, res) => {
		res.json(
			{ time: Date.now() }
		);
	}
}
```

## Static Pages
In order to use static pages, you must add `public` to your options settings.
Create a directory named `public` in your root project directory. This is where you can put CSS, JS, Images, HTML, etc.

## Opening the server
Once you have entered the settings into your base file, you can now start the server.
In order to start the server, inside your base root index file, beneath the settings initialization, add:
```js
jank.listen();
```

Now if you type `npm install` into the terminal of your root project directory, it will install all the required dependencies for running the project.
Enter `node <file>` into the terminal and now your server will start.
