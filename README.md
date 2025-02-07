# Negative External Influence Recognition
####Project Status: More Work Needed

## Project Objective
* The goal for this project is to train a neural network to determine whether individual residential properties suffer from negative external influence.
* The model will take in satellite images of individual properties and output “Adverse” if the property's surroundings adversely affect its value, or “Neutral” if the location has a neutral or positive affect on value.

### What is Negative External Influence?
* When a property's value is negatively affected by its surroundings it is a called negative external influence. Negative influence typically occurs when a property is near a busy road/highway, commercial property, train tracks, etc. and adversely impacts the value of a property.

## Dataset
* I manually collected 500 satellite images of residences from Google Earth and sorted them 50/50 by properties with Neutral and Adverse external influences
* Each photo has a red marker denoting the exact location of the property, and was collected using the same scale settings to ensure the images would be as uniform as possible
* The addresses are randomly distributed nationwide and contain examples of properties from a myriad of different surroundings (suburban, rural, urban, etc.)

## Preprocessing
* The images were processed using ResNet preprocessing in batches of five and resized to 255x255 and then split into training and validation batches using an 80/20 split.
* Data augmentation was impllemented after two inital models badly overfit and failed to generalize

## Project Results
* Best model was a fine-tuned Xception Model (pre-trained Keras model): 74% accuracy on the validation set

## Ideas for Further Refinement
* Try boundary boxes around things that represent negative invfuence then measuring the distances from the homes to the boundary box, since Convnets are location invariant.
* Try more zoomed in images of the homes
* Switch scoring metric to recall and attempt to flag 100% or residences with potentially adverse locations. This makes more sense if model was utilized in a professional setting
