# GAN_MNIST

In this project, the least squares generative adversarial netowrks and deeply convolutional generative adversarial networks are implemented to generate images from the MNIST data set. 

In a GAN, we build two different neural networks. Our first network is a traditional classification network, called the discriminator. We will train the discriminator to take images, and classify them as being real (belonging to the training set) or fake (not present in the training set). Our other network, called the generator, will take random noise as input and transform it using a neural network to produce images. The goal of the generator is to fool the discriminator into thinking the images it produced are real.

We can think of this back and forth process of the generator (G) trying to fool the discriminator (D), and the discriminator trying to correctly classify real vs. fake as a minimax game:

minimizeGmaximizeDEx∼pdata[logD(x)]+Ez∼p(z)[log(1−D(G(z)))]

where z∼p(z) are the random noise samples, G(z) are the generated images using the neural network generator G, and D is the output of the discriminator, specifying the probability of an input being real. In Goodfellow et al., they analyze this minimax game and show how it relates to minimizing the Jensen-Shannon divergence between the training data distribution and the generated samples from G.

To optimize this minimax game, we will aternate between taking gradient descent steps on the objective for G, and gradient ascent steps on the objective for D:

1 - Update the generator (G) to minimize the probability of the discriminator making the correct choice.
2 - Update the discriminator (D) to maximize the probability of the discriminator making the correct choice.

CONCLUSIONS:
1 - The LSGAN produces better images than the GAN loss function.

2 - The output of the DCGAN network has much less noise compared to the noise present in the simple GAN network.

3 - Quantitatively evaluating the GAN model can be done by training the generator to maximize the probability of the discriminator classifying it as an image from the mnist dataset.
