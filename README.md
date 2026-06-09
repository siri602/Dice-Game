# 🎲 Dice Game

A two-player dice game that runs in the browser. Each player rolls a die on page load — highest number wins. Built with plain HTML, CSS, and JavaScript. No frameworks, no dependencies.

---

## How It Works

The entire game logic lives in `index.js` and runs automatically when the page loads.

### 1. Generating a random dice number

```js
var randomNumber1 = Math.floor(Math.random() * 6) + 1;
```

- `Math.random()` returns a decimal between `0` and `0.999...`
- Multiply by `6` → `0` to `5.999...`
- `Math.floor()` rounds down → `0` to `5`
- `+ 1` shifts the range → **1 to 6**

The same logic runs twice — once for each player.

---

### 2. Swapping the dice image

```js
var randomDiceImage = "dice" + randomNumber1 + ".png";
var randomImageSource = "images/" + randomDiceImage;

var image1 = document.querySelectorAll("img")[0];
image1.setAttribute("src", randomImageSource);
```

- Builds a filename like `dice3.png` from the random number
- Selects the first `<img>` on the page with `querySelectorAll("img")[0]`
- Updates its `src` attribute to point to the matching image in the `images/` folder

Player 2's image is updated the same way using `querySelectorAll("img")[1]`.

---

### 3. Announcing the winner

```js
if (randomNumber1 > randomNumber2) {
  document.querySelector("h1").innerHTML = "Player 1 Wins!";
} else if (randomNumber2 > randomNumber1) {
  document.querySelector("h1").innerHTML = "Player 2 Wins!";
} else {
  document.querySelector("h1").innerHTML = "Draw!";
}
```

Compares the two numbers and updates the `<h1>` heading with the result. Three possible outcomes: Player 1 wins, Player 2 wins, or a draw.

---

## File Structure

```
dice-game/
├── index.html       ← page structure
├── styles.css       ← layout and styling
├── index.js         ← all game logic
└── images/
    ├── dice1.png
    ├── dice2.png
    ├── dice3.png
    ├── dice4.png
    ├── dice5.png
    └── dice6.png
```

---

## Running It

No setup needed.

```bash
open index.html
```

Or just drag `index.html` into any browser. The dice roll automatically on every page load or refresh.

---

## Re-rolling

The game re-rolls every time the page refreshes — press **Cmd+R** / **F5** to play again.

To add a button instead, wrap the logic in a function and call it on click:

```js
function rollDice() {
  // move all the logic here
}

document.querySelector("button").addEventListener("click", rollDice);
```
