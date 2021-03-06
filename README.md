# MLP character recognition

Trains a multi-layer perceptron (MLP) neural network to perform optical character recognition (OCR).

The training set is automatically generated using a highly modified version of the captcha-generator [node-captcha](http://npmjs.com/package/node-captcha).

The network takes a 20x20-bit (400-bit) one-dimensional binary array as input and outputs an 8-bit binary array, which can then be converted into a character code. Initial performance measurements show promising success rates.

After training, the network is saved as a standalone module to ```./network.js```, which can then be used in your project with

```javascript
var network = require('./network.js');
var output = network.activate(input);
```

## Performance

### abcdefghijklmnopqrstuvwxyz

* **Font:** Arial, Helvetica, sans-serif
* **MLP specification:**
  * **Neurons:** (```400``` input, ```40``` hidden, ```8``` output)
  * **Learning rate:** ```0.1```
  * **Training set:**
    * **Size:** ```52000``` characters
    * **Sample:** ![abcdefghijklmnopqrstuvwxyz](https://raw.github.com/mateogianolio/mlp-character-recognition/master/examples/abcdefghijklmnopqrstuvwxyz.png)
  * **Testing set:**
    * **Size:** ```52000``` characters
* **Measured success rate:** ```98.52884615384615%``` (of 52000 inputs from testing set)
    
### 0123456789

* **Font:** Arial, Helvetica, sans-serif
* **MLP specification:**
  * **Neurons:** (```400``` input, ```40``` hidden, ```8``` output)
  * **Learning rate:** ```0.1```
  * **Training set:**
    * **Size:** ```20000``` characters
    * **Sample:** ![0123456789](https://raw.github.com/mateogianolio/mlp-character-recognition/master/examples/0123456789.png)
  * **Testing set:**
    * **Size:** ```20000``` characters
* **Measured success rate:** ```99.66%``` (of 20000 inputs from testing set)

## Usage

Clone this repository. The script is using [canvas](https://www.npmjs.com/package/canvas), so you'll need to install the **Cairo** rendering engine. On OSX, this can be done with the following one-liner (copied from canvas README):

```bash
$ wget https://raw.githubusercontent.com/LearnBoost/node-canvas/master/install -O - | sh
```

Then install npm dependencies and test it:

```bash
$ npm install
$ node main.js
```

## Example

Here is an example run of the script:

```bash
$ node main.js
generating images ...
... done

neural network specs:
  layers:
    input: 400 neurons.
    hidden: 40 neurons.
    output: 8 neurons.
  learning rate: 0.1
  training set: 52000 characters.
  testing set: 52000 characters.

learning ...
progress: 10%
progress: 20%
progress: 30%
progress: 40%
progress: 50%
progress: 60%
progress: 70%
progress: 80%
progress: 90%
... done

network saved to ./network.js

testing on 52000  samples ...
progress: 10%
progress: 20%
progress: 30%
progress: 40%
progress: 50%
progress: 60%
progress: 70%
progress: 80%
progress: 90%
... done

success rate: 98.52884615384615 %
```

## Todo

* Add customizability (fonts, optional distortion, MLP specs, threshold etc.)
* Add training based on target success rate

## Contribute

Feel free to fork and submit pull requests.