---
title: "How to make and install the image of my own Ubuntu 16.04 installation with Docker on"
date: 2020-03-24
forum: General Help
---

### Post by marietto2008 on 2020-03-24
I'm going to hire some space on a remote linux workstation equipped with a Geforce GTX 1080 ti because I want to run there this deep learning repository :

[https://github.com/CMU-Perceptual-Computing-Lab/MonocularTotalCapture](https://github.com/CMU-Perceptual-Computing-Lab/MonocularTotalCapture)

It requires Ubuntu 16.04 and Cuda 9 to run and my graphic card (Geforce RTX 2080 ti) does not support it. I have also another computer with a Geforce 1060. I have installed the repo on that computer,but when I run it It always give this error to me :

./openpose/build/examples/openpose/openpose.bin --face --hand --image_dir ./example_dance/raw_image --write_json example_dance/openpose_result --render_pose 0 --display 0 -model_pose BODY_25 -Starting OpenPose demo...Configuring OpenPose...Starting thread(s)...Auto-detecting all available GPUs... Detected 1 GPU(s), using 1 of them starting at GPU 0.F0322 22:31:40.377177 10803 syncedmem.cpp:71] Check failed: error == cudaSuccess (2 vs. 0)  out of memory

*** Check failure stack trace: ***    @     0x7f9f2800e5cd  google::LogMessage::Fail()    @
    
I suppose that that PC is not enough powerful to run the repository. I've contacted a company that told me that I should "install my image to our server using docker container". They also say that they haven't a specific tutorial that I can follow to learn how to do that. Since I'm not a pro,I'm an hobbyst,I'm here to ask if someone has some specific tutorial to do what I want.

I've already been able to make work the Monocular Total Capture repository. But I'm not able to repeat all the steps because I've been lucky. I gone through trial and errors. For this reason I want to clone my existing ubuntu installation and make a docker image of everything that's inside of it

---

