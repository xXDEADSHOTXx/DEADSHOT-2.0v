

# Lab Assistant by deadshot
This is a browser-based script to track status and automate actions within SAGE Labs.

Current features:
* Automated scanning with timers which respect SDU discovery rules
  * Supports multiple fleets
  * Utilizes your fleet's specific scan timer
  * Utilizes a 2 min timer if an SDU is discovered
  * Does not interfere with other user activity
* Automated resupply
  * When the fleet has less than 10 tools, it will return to the designated starbase
  * Transfer SDUs from the fleet to the starbase
  * Refuel the fleet
  * Restock the fleet with toolkits
  * Warp to the designated scanning sector and resume scanning
* Automated mining [WIP]
* Automated transportation [WIP]
* Surveillance courtesy of SkyLove512

### SECURITY NOTICE
Users are encouraged to build their own instance of browser-compatible resource file. Doing so ensures that you are using trusted code. Pre-built files are provided for convenience. 

### Building your own browserified version
This script uses a browserified versiosn of Anchor, bs58, and Buffer. 

```
browserify anchor-input.js --standalone BrowserScore -p esmify --exclude process -o anchor-browserified.js
```

anchor-input.js
```
const anchor = require("@coral-xyz/anchor");
module.exports = {anchor};
```

buffer-input.js
```
const Buffer = require("buffer");
module.exports = {Buffer};
```

bs58
```
browserify node_modules/bs58/index.js -o bs58.bundle.js --standalone bs58
```

### Known Bugs
* You must manually load at least one item onto a Starbase before the script can interact with that Starbase
* Scanning does not support multi-jump warping. The distance between the Target and Starbase must be within 1 warp *or* you must select the Subwarp config option.

### Usage
The script is built as a TamperMonkey script. [TamperMonkey](https://www.tampermonkey.net/) is a userscript manager available for free as a browser extension.

#### Setup
1. Install TamperMonkey
2. Select the SLY_Lab_Assistant.user.js file in this repo. View the file and click the "Raw" button to view its source.
3. Copy the source
4. Open Tampermonkey in your browser and click the Add Script tab (icon with a plus symbol)
5. Paste the source into the script window and click File > Save
6. Browse to [https://labs.staratlas.com/](https://labs.staratlas.com/)
7. Launch the game as normal
8. Click the Lab Assistant "Configure" button
9. For each fleet that you want Lab Assistant to help with, click the Scan checkbox and fill in the destination and starbase coordinates.
   * Enter coordinates as two numbers separated by a comma with no bracks or prefixes or parenthesis - i.e. 10,20
11. Slick save then refresh your browser

#### Troubleshooting
1. It's best to do everything once manually. If you form a new fleet for mining, do one round of manual loading, mining, and unloading.
   * SAGE involves *a lot* of token accounts. One manual round ensures that these token accounts get properly initialized.
   * Ideally Lab Assistant will handle this, but as it's still a WIP this is the most likely area to still have some bugs.
2. If you're not sure if something worked, check the blockchain for errors.
3. If you're pretty sure something broke, check the browser console for errors.
4. Visit SLY's discord or reach out to justgroove.

#### Regular usage
1. Launch the game as usual
2. Click the Lab Assistant "Start" button
3. __Leave the browser window open (it can be minimized)__ - this is required since the script runs in the browser

## Contact Information

Our website: https://sly.cyclic.app/

Our discord: https://discord.gg/DCD9CuJFRr

Our github: https://github.com/ImGroovin

If you'd like to tip/donate/buy the devs a beer/coffee, our Solana address: SLYxadUPv6gnFRBKj7UxZytGYbLdAtUHn4TTLMj1dmL
