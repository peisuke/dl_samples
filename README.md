# Deep Learning frameworks comparison on CPU

This repository is test code for comparison of several deep learning frameworks. 
The target models are VGG-16 and MobileNet. All sample code have docker file, and
the test environment is easy to set up. Currently, the parameters of each network 
are randomly generated. I have not confirm the result is correct yet. 
I will implement weight importing as soon as possible.

## About

In this repository, the compared frameworks are as below.
- [Caffe](http://caffe.berkeleyvision.org/) : [repo](https://github.com/BVLC/caffe)
- [Caffe2](https://caffe2.ai/) : [repo](https://github.com/caffe2/caffe2)
- [Chainer](https://chainer.org/) : [repo](https://github.com/chainer/chainer)
- [Mxnet](https://mxnet.incubator.apache.org/) : [repo](https://github.com/apache/incubator-mxnet)
- [Tensorflow](https://www.tensorflow.org/) : [repo](https://github.com/tensorflow/tensorflow)
- [Pytorch](http://pytorch.org/) : [repo](https://github.com/pytorch/pytorch)
- [NNabla](https://nnabla.org/) : [repo](https://github.com/sony/nnabla)
- [CNTK](https://www.microsoft.com/en-us/cognitive-toolkit/) (Not yet) : [repo](https://github.com/Microsoft/CNTK/)
- [Theano](http://deeplearning.net/software/theano/) (Not yet) : [repo](https://github.com/Theano/Theano)

I prepared various setup condition about the frameworks, 
e.g. with/without MKL, pip or build.

## How to

Download Dockerfile and run it.

```
$ docker build -t {NAME} .
$ docker run -it --rm {NAME}
```

NAME is an arbitrary docker image name defined by the user. It is only used for managing created docker images.
In the created docker containor, clone the repository and run test code.

```
# git clone https://github.com/peisuke/DeepLearningSpeedComparison.git
# cd DeepLearningSpeedComparison/{FRAMEWORK}/vgg16
# python3 (or python) predict.py
```

## Current results

__Currently, the results are not reliable. As soon as possible, I will check my code.__

```
caffe(atlas, 1.0)
caffe-vgg-16 : 13.900894 (sd 0.416803)
caffe-mobilenet : 0.121934 (sd 0.007861)

caffe(openblas, 1.0)
caffe-vgg-16 : 3.308656 (sd 0.043299)
caffe-mobilenet : 0.098129 (sd 0.011925)

caffe(mkl, 1.0)
caffe-vgg-16 : 3.005638 (sd 0.129965)
caffe-mobilenet: 0.044592 (sd 0.010633)

caffe2(1.0)
caffe2-vgg-16 : 1.351302 (sd 0.053903)
caffe2-mobilenet : 0.069122 (sd 0.003914)

caffe2(mkl, 1.0)
caffe2-vgg-16 : 0.526263 (sd 0.026561)
caffe2-mobilenet : 0.041188 (sd 0.007531)

mxnet(1.3.0)
mxnet-vgg-16 : 0.505703 (sd 0.169324)
mxnet-mobilenet : 0.041478 (sd 0.005498)

mxnet(1.3.0, mkl)
mxnet-vgg-16 : 0.114950 (sd 0.188471)
mxnet-mobilenet : 0.009650 (sd 0.007492)

pytorch(0.4.1)
pytorch-vgg-16 : 0.546202 (sd 0.008096)
pytorch-mobilenet : 0.113275 (sd 0.006721)

nnabla(0.9.5)
nnabla-vgg-16 : 1.444331 (sd 0.023142)
nnabla-mobilenet : 4.267674 (sd 0.043402)

tensorflow(pip, v1.10.1)
tensorflow-vgg-16 : 0.206103 (sd 0.011668)
tensorflow-mobilenet : 0.045416 (sd 0.002605)

tensorflow(opt, r1.10.1)
tensorflow-vgg-16 : 0.164266 (sd 0.010878)
tensorflow-mobilenet : 0.039643 (sd 0.002287)

tensorflow(opt, XLA, r1.3)
tensorflow-vgg-16 : 0.151689 (sd 0.006856)
tensorflow-mobilenet : 0.022838 (sd 0.007777)

tensorflow(mkl, r1.0)
tensorflow-vgg-16 : 0.163384 (sd 0.011794)
tensorflow-mobilenet : 0.034751 (sd 0.011750)

chainer(4.4.0)
chainer-vgg-16 : 0.582105 (sd 0.019283)
chainer-mobilenet : 0.096270 (sd 0.020240)

chainer(4.4.0, ideep4py)
chainer-vgg-16 : 0.089582 (sd 0.013343)
chainer-mobilenet : 0.058015 (sd 0.011278)
```
