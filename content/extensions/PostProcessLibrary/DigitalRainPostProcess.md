# Using the Digital Rain post-process

How cool (... or nerd - ish) could it be to render all your BJS scene in a Digital Rain Fall?

If you would like it, this tutorial is made for you.

## How to use ?

Digital Rain Post Process Scripts can be found here: 
- Normal: [https://github.com/BabylonJS/Babylon.js/blob/master/postProcessLibrary/dist/babylon.digitalRainPostProcess.js](https://github.com/BabylonJS/Babylon.js/blob/master/postProcessLibrary/dist/babylon.digitalRainPostProcess.js)
- Minified : [https://github.com/BabylonJS/Babylon.js/blob/master/postProcessLibrary/dist/babylon.digitalRainPostProcess.min.js](https://github.com/BabylonJS/Babylon.js/blob/master/postProcessLibrary/dist/babylon.digitalRainPostProcess.min.js)

Please, first reference this script in your page:

```
	<script src="babylon.digitalRainPostProcess.js"></script>
```

Then, you only need to instantiate the post process attach to your main camera to bring it to life.

```
// Creates the post process
var postProcess = new BABYLON.DigitalRainPostProcess("DigitalRain", camera);
```

[**Playground Demo Scene**](http://babylonjs-playground.com/#2I28SC#6)

## Going further

The first you can do is changing the font used in the post process.

```
// Creates the post process
var postProcess = new BABYLON.DigitalRainPostProcess("DigitalRain", camera, "3px Monospace");
```

[**Playground Demo Scene**](http://babylonjs-playground.com/#2I28SC#7)

But you could also play with more parameters:

```
// Creates the post process
var postProcess = new BABYLON.DigitalRainPostProcess("DigitalRain", camera, 
    {
        font: "30px Monospace",
        mixToNormal: 0.5,
        mixToTile: 0.5        
    });
```

[**Playground Demo Scene**](http://babylonjs-playground.com/#2I28SC#8)

The availables parameters are:

- font: the font to use defined the W3C css way like "30px Monospace". Note: a monospace font would provide better result.
- mixToNormal: defines the amount you want to mix the "tile" or caracter space colored in the digital rain (between 0 and 1).
- mixToTile: defines the amount you want to mix the normal rendering pass in the digital rain (between 0 and 1).

Two of them mixToNormal and mixToTile are also available at run time to allow smoothly fading from matrix to your normal scene.

```
// Creates the post process
var postProcess = new BABYLON.DigitalRainPostProcess("DigitalRain", camera);
// Displays the scene.
var alpha = 0;
scene.registerBeforeRender(function() {
    alpha += 0.01;
    postProcess.mixToNormal = Math.cos(alpha) * 0.5 + 0.5; // between 0 and 1.
});
```

[**Playground Demo Scene**](http://babylonjs-playground.com/#2I28SC#9)
