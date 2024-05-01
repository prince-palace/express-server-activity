# Express Server Activity

For this activity, you will be going through the same steps from lecture. You will always be able to reference notes when creating a server, there is no need to memorize these steps. Focus on the big picture and making sure everything is setup correctly. When you are done, your site should be viewable on http://localhost:5001


## Setup Instructions

1. **Use this template** to create a GitHub repo on your account
2. Clone the repo on to your computer
3. Create a `.gitignore` file and ignore `node_modules/`, `.DS_Store` and `*.log`
  
  **.gitignore**

  ```
  node_modules/
  .DS_Store
  *.log
  ```

4. In the project folder, run `npm init --yes`
5. Install express `npm install express`
6. If you made a mistake, that's ok, you can always `npm uninstall some-thing`

> NOTE: Some lecture notes and assignments will reference `body-parser`. This library is now included as a part of `express`.

## Add HTML, CSS & JavaScript

You will need to move the existing HTML, JS and CSS files into a folder named `public`.

Folder structure:

  ```
  salary-calculator-server/
  ├── server/
  │   ├── public/
  │   │   ├── scripts/
  │   │   │   └── client.js
  │   │   ├── styles/
  │   │   │   └── style.css
  │   │   └── index.html
  │   └── server.js
  ├── node_modules/
  │   ├── express/
  │   └── ...
  └── .gitignore
  ```

  > NOTE: The `node_modules` folder is auto generated.

## NPM

Notice above we are using a program called `npm` to install things called 'packages.'

[Node Package Manager](https://www.npmjs.com/) 

>npm is the package manager for JavaScript and the world’s largest software registry. Discover packages of reusable code — and assemble them in powerful new ways.

NPM allows us to use code written by others or even to share our own Node project. Much like we use jQuery, which is code written by someone else to save time and effort. NPM is a registry (and a tool) to help manage and access a ton of pre-made code. In fact, we can install jQuery using `npm`! Most popular packages can be installed via the `npm` tool.

## Setup Our Server

**server.js**

```JavaScript
// Require express - gives us a function
const express = require('express');

// Create an instance of express by calling the function returned above - gives us an object
const app = express();
const port = process.env.PORT || 5001;

// express static file serving - public is the folder name
app.use(express.static('server/public'));

// Start up our server
app.listen(port, () => {
  console.log('listening on port', port);
});
```

At this point we could start our server using `node server/server.js`. To simplify things we can add the following line to our `package.json` file.

**package.json**

```json
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "node server/server.js"
  },
```

Now we can start the server with `npm start`. Keep in mind, only one thing can be listening on a specific port. If you already have a server running on port 5001, you will either need to stop that server or change your port number.

### Stopping a Node Server

You will need to restart the server each time you make changes to the `server.js` file. Press `ctrl-c` in terminal to stop the server.

To stop ALL Node servers running on your computer, you can type `killall node` in terminal. 

## Testing the Server

You should be able to run your code by navigating to [http://localhost:5001](http://localhost:5001).


## Stretch Goals

### Add a Photo

Put some photos in your `public` folder and add them to your `index.html`. Try navigating to your photo directly from the browser (http://localhost:5001/photos/YOUR_PHOTO.jpg).

### Create a GET route

Our server currently returns static files (HTML, CSS & JS). Next week, we will be using servers to return different types of data. Add the following to your `server.js`:

```js
app.get('/hello', (req, res) => {
  res.send('Hello World!');
});
```

Navigate to http://localhost:5001/hello and see what happens. What happens if you replace the string 'Hello World!' with an Array of data? We will cover this topic in more detail next week.
