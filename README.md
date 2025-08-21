# Fire Intro Effect

A PICO-8 tech demo recreating the DOOM fire effect, running at a stable 60 FPS. This project simulates a flickering flame wall that spreads from bottom to top.

## About

This tech demo showcases the iconic fire effect inspired by the DOOM intro, implemented within the constraints of the PICO-8 fantasy console. It achieves smooth 60 FPS performance through careful optimization, making it a great example of working within PICO-8's limitations.

## Files

* **fireintro.p8**: The PICO-8 cartridge file containing the source code and assets. Load this in PICO-8 to run or edit the demo.
* **fireintro.p8.png**: A PNG version of the cartridge, which can be loaded into PICO-8 by dragging the image into the editor.

## Technical Challenges

There aren't many detailed resources or tutorials online for implementing such effects efficiently. Many examples are too simplistic, requiring significant trial and error to stay within constraints. This project uses a 2D array for fire intensities, updated per frame, with optimized drawing by rendering pixels in four sections to save computation time.

## Implementation Highlights

* **Initialization**: A 32x36 pixel grid is filled with minimal intensity; the bottom row starts at white (maximum intensity).
* **Update**: In `_update60()`, fire spreads upward by randomly decreasing and propagating intensity values.
* **Reduced Resolution:** The fire effect is computed on a low-resolution 32x36 grid (1152 pixels). This drastically reduces the number of calculations in the _update60() function, which updates fire intensities.
* **Pixel Scaling:** Instead of computing unique pixel values for the entire screen width, the code reuses each pixel from the 32x36 grid four times horizontally (w, w*2, w*3). This "stretching" creates a full-screen effect without additional computation.
* **Minimal pset Calls:** By only calling pset for non-zero colors (col > 0) and drawing four pixels at once, the code minimizes the number of loop iterations and draw operations.

## How to Run

1. Download the `fireintro.p8` or `fireintro.p8.png` file.
2. Open PICO-8 and load the cartridge:
   * For `.p8`: Use `load fireintro.p8` in the PICO-8 console.
   * For `.p8.png`: Drag the PNG file into the PICO-8 editor.
3. Type `run` to start the demo.

## Contributing

Feel free to fork this repository, experiment with optimizations, or add new features! If you have suggestions or improvements, open an issue or submit a pull request.

## Disclaimer

This project is a technical demo inspired by the fire effect seen in DOOM and does not use any assets or code from the original game.
