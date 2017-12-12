# twitter-like

The goal of this project is to build a *twitter-like* JavaScript application.

## Requirements

- node v9+: https://nodejs.org/en/download/current/
- Chrome v61+ / Firefox 54+

## Instructions

### Back-End

`server` directory is used to serve a REST API with one endpoint: `/tweets`. To start it, go to `server` with your terminal (`cd path/to/server`) and download dependencies by running: `npm install`. Then run `npm start`. Tweets (in JSON format) should be available on `http://localhost:3000/tweets` (check on your browser).

### Front-End

Your JavaScript code will be written within `app/scripts` with ES2015 modules. Entry point is `script/index.js` as specified in `index.html`:
```html
<script type="module" src="scripts/index.js"></script>
```
**Thus, be sure to use Chrome v61+ or Firefox 54+ (with `dom.moduleScripts.enabled` activated in `about:config`).**

#### live-server

Because of ES2015 modules and ajax requests, the app needs a http server to run correctly. Install `live-server` (globally): `npm install -g live-server`. Then go to `app` with your terminal and run: `live-server`. Your default browser should automatically open at `http://127.0.0.1:8080/`. From now on, every code you write within `app` will trigger a live reload, which means you don't need to refresh your page to see the last results.

## Assignments

There are 3 steps that needs to be completed:

1. Fetch and render tweets
2. Display a tweet in a modal on click
3. Post new tweets

### Fetch and render tweets

You will use standard `fetch` API (with a `GET` method) to get tweets from `http://localhost:3000/tweets`. The list should be ordered by `id` in `desc` order. You can use lodash `_.orderBy` function (lodash is already included in index.html). A tweet should be rendered with the following HTML code:

```html
<div class="tweet">
  <img class="avatar" src="[avatar]">
  <div>
    <div class="tweet-header">
      <span class="fullname-group">
        <strong class="fullname">[fullname]</strong>
        <span class="username">[username]</span>
      </span>
    </div>
    <div class="tweet-text">
      <p>[text]</p>
    </div>
  </div>
</div>
```
Values between `[]` represent the names of the corresponding fields in a tweet object. They should be replaced with real tweet data. Each tweet element is a child of `<div class="container">` tag. Each tweet avatar should be fetched by prefixing `http://localhost:3000/` to the `tweet` object `avatar` field.

**The code that handles `http://localhost:3000/tweets` call should be in its own JavaScript module.**

#### Expected result 👇

<img src="https://sciences-u-lyon.github.io/twitter-like/tweets.png" width="600">

### Display a tweet in a modal on click

On each tweet, a click event should open a modal window. The modal simply shows the tweet in larger size. It should be closed on background (the overlay window) click event. A modal is defined with the following HTML code:

```html
<div class="modal-overlay">
  <div class="modal-content">
    <div class="tweet is-modal">
      ...
    </div>
  </div>
</div>
```

The code within `<div class="tweet is-modal">` is the same code than the one used to render a tweet in the list.

**The code that handles the modal should be in its own JavaScript module.** Export a `Modal` class that takes a tweet object in its constructor. It should have an `open` method (add `<div class="modal-overlay">` to document `body`) and a `close` method (remove `<div class="modal-overlay">`).

#### Expected result 👇

<img src="https://sciences-u-lyon.github.io/twitter-like/modal.png" width="600">

### Post new tweets

The input field should be used to create and add a new tweet to the list, on `enter` key touch event.

Create a `tweet` object with the input value as the tweet `text` and random `fullname` and `username` values. You don't need to set an `id` and an `avatar`.

Post this `tweet` object using standard `fetch` API with a `POST` method on `http://localhost:3000/tweets`. Reload the page after the tweet was posted. You should use the default avatar for the new tweets, available at `http://localhost:3000/img/avatar.jpg`.

**The code that handles the `POST` call should be in the appropriate JavaScript module.**

#### Expected result 👇

<img src="https://sciences-u-lyon.github.io/twitter-like/new-tweet.png" width="600">

# Good Luck! 😉
