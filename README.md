# floaty-cloud
A offline game by Google.

## How to play
As you turn out when there's no Internet connection on Google app, a offline game will be appear called "Floaty Cloud", which it's a game where you tap (or click) to jump and avoid obstacles (like enemies). After you touch a enemy, the game ends and shows your score what you got!

## How we've discovered
We also discovered the offline game folder called "puffygame" from Google app .apk file extracted, which it's from "assets" folder, but so it's very easy to find, eh?\
After you extracted the .apk file, you could see their contents of Google app data. Tap "assets" if is it there, then you tap "puffygame", and you will find behind of offline game!

Exactly, the offline game can be modified by editing puffy.js file. Here you can change Floaty Cloud enemies and player, you can usually make the game to scroll faster and the player too.\
First, you find a text from puffy.js section.
```javascript
this.o.i=60;this.i.j=60;
```
**i** means the background speed\
The background speed will just glitch if there's large value in it, the clouds will just cut down, and the scale will just cut down too than paradox scroll.\
**j** means the player "puffy" speed\
Putting Infinity or any speed without changing the background, the player won't die unless it will appear whereabouts. It keeps counting, but falling or touch an enemy won't die though.

### Enemy spawning
Enemy spawning can be changed by finding:
```javascript
Rc.prototype.update=function(a){0<this.i&&(this.i-=a,0>=this.i&&this.j())}
```
In start of function, you notice **0** in the start. It means if the game ends, update the score. If you change 0 into 1, the game will just hit and won't continue the score.\
In =a,0, you notice there's some spawning value, if you put into 100, game tries to render the enemies if there's more enemies in this game but it's not winnable. Put into 0 for normal gameplay.

### Miscellaneous
There's some things to that player:
```javascript
this.i.i=-180;this.i.H=288
```
**i** means the player bouncing power\
**H** means the player falling power\
```javascript
new xc(b,function(){return 0<a.i.i?0:1})
```
A player sprite can be changed by the end of colons. 0:1 is also mean if client taps the player to jump, the sprite will change and revert back then.
```javascript
this.T+=.005*a,this.H+=50*a)
```
**T** means the time speed\
**H** means the score limit from scrolling
```javascript
new Hc(c),0>e.i||e.j>Q())c=!0;else{for(g=0;g<d.length;g++)if(c!==d[g])
```
At "c=!0", you can disable dying from walls.\
At "g=0", you can disable dying from enemies.\
**Others will be soon.**
