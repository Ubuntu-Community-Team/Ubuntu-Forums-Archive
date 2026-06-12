---
title: "How to downgrade from GCC 5.4.0 to GCC 5.3.1 in ubuntu 16.04 ?"
date: 2018-02-21
forum: General Help
---

### Post by papatya2 on 2018-02-21
I would try to install tensorflow.
I installed Cuda Toolkit 9.1.

I tried to install cuDNN properly :
cuDNN v7.0.5 Runtime Library for Ubuntu16.04 (Deb)
cuDNN v7.0.5 Developer Library for Ubuntu16.04 (Deb)
cuDNN v7.0.5 Code Samples and User Guide for Ubuntu16.04 (Deb)
...

$ ./mnistCUDNN

cudnnGetVersion() : 7005 , CUDNN_VERSION from cudnn.h : (7005) (7.0.5)
Cuda failurer version : GCC 5.4.0
Error : unknown error
error_util.h:93
Aborting...

So I think cuDNN isn't installed properly.
How can it be solved ?

Ubuntu 16.04.9 : Ubuntu 5.4.0-6ubuntu1 : GCC 5.4.0
GPU GTX 1080 ti
64 bit
NVIDIA Driver 390.25 : NVIDIA-Linux-x86_64-390.25.run
CUDA Toolkit 9.1
Python3.6.4

---

### Post by wildmanne39 on 2018-02-21
*Thread moved to **General Help, a more appropriate forum**.* because Installation and Upgrades forum is only for > For questions about upgrading and installation of your new Ubuntu OS.


---

### Post by papatya2 on 2018-02-21
So how can make it run ?

---

### Post by wildmanne39 on 2018-02-21
You will need to wait for someone that can answer your question to be online, the forum is made up of volunteers from all over the world so it is possible the person that has the answer is sleeping.

Please only bump your thread once every twelve hours.

---

### Post by #&amp;thj^% on 2018-02-21
> **wildmanne39 said:**
> You will need to wait for someone that can answer your question to be online, the forum is made up of volunteers from all over the world so it is possible the person that has the answer is sleeping.

Please only bump your thread once every twelve hours.
+1
And not many will help with installing Drivers from nvidia instead of from our Repos or PPAs. "NVIDIA-Linux-x86_64-390.25.run"

---

### Post by papatya2 on 2018-02-21
I think it maybe related to gcc version.
Gcc5.3.1 is supported one. I have gcc5.4.0.
So how can it be updated to old one ?

---

### Post by papatya2 on 2018-02-22
Cuda doesn't support GCC 5.4.0.
How to downgrade from GCC 5.4.0 to GCC 5.3.1 in ubuntu 16.04 ?

$ ./mnistCUDNN

cudnnGetVersion() : 7005 , CUDNN_VERSION from cudnn.h : (7005) (7.0.5)
Cuda failurer version : GCC 5.4.0
Error : unknown error
error_util.h:93
Aborting...

Ubuntu 16.04.9 : Ubuntu 5.4.0-6ubuntu1 : GCC 5.4.0
CUDA Toolkit 9.1
Python3.6.4

[COLOR=#333333][FONT=DINWebPro][/FONT][/COLOR]

---

### Post by cruzer001 on 2018-02-22
Version numbers look off:

[https://packages.ubuntu.com/xenial/gcc](https://packages.ubuntu.com/xenial/gcc)

---

### Post by papatya2 on 2018-02-22
So what are commands for installation ?

---

### Post by cruzer001 on 2018-02-22
Install what?  4:5.3.1 is default install for 16.04.  There is no 5.4.0.  I say again, your version numbers are off/incorrect.

Check your policy:
```
apt policy gcc
```

Also please post the output of:
```
inxi -S
```

---

### Post by cruzer001 on 2018-02-22
Found it.  A PPA  Is this how you installed it?

You can remove PPAs with "ppa-purge".

---

### Post by steeldriver on 2018-02-22
I believe 5.4.0 is provided by xenial-updates - this is what I see on my 16.04 box. The best known PPA (toochain-r) provides 5.4.1

```

$ apt-cache policy gcc-5
gcc-5:
  Installed: 5.4.1-2ubuntu1~16.04
  Candidate: 5.4.1-2ubuntu1~16.04
  Version table:
 *** 5.4.1-2ubuntu1~16.04 500
        500 http://ppa.launchpad.net/ubuntu-toolchain-r/test/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
     5.4.0-6ubuntu1~16.04.9 500
        500 http://ca.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
     5.3.1-14ubuntu2 500
        500 http://ca.archive.ubuntu.com/ubuntu xenial/main amd64 Packages

```

(I don't think you can rely on apt policy gcc since it's a dependency package.)

---

### Post by cruzer001 on 2018-02-22
Thanks steeldriver :)

---

### Post by papatya2 on 2018-02-23
I will try and let you know.

---

### Post by steeldriver on 2018-02-23
Apologies - my comment above was really just trying to clarify the versions

I don't really know "How to downgrade from GCC 5.4.0 to GCC 5.3.1 in ubuntu 16.04" once your repositories have pushed you up to 5.4.0 - my *guess *is it will actually be easier to upgrade to the next supported compiler (possibly gcc-6.3.0) which should be available from the toolchain-r PPA

However I'm not really sure what CUDA version you have or what its requirements are - I can't find any mention of version 7.0.5 in the compiler support matrices online

---

### Post by papatya2 on 2018-02-25
$ apt policy gcc
gcc : Installed : 4:5.3.1-1ubuntu1
        Candidate : 4:5.3.1-1ubuntu1
        Version table :
*** 4:5.3.1-1ubuntu1 500
     500 [http://tr.achive.ubuntu.com/ubuntu](http://tr.achive.ubuntu.com/ubuntu) xenial/main amd64 Packages
     100 /var/lib/dpkg/status

$ inxi -S
  No command 'inxi' found

$ apt-apt-cache policy gcc-5
gcc-5:
    Installed:5.4.0-6ubuntu1~16.04.9    
    Candidate:5.4.0-6ubuntu1~16.04.9
    Version table:
*** 5.4.0-6ubuntu1~16.04.9 500
    500 [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages
    500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 Packages
    100 /var/lib/dpkg/status
   5.3.1-14ubuntu2 500
    500 [http://tr.archive.ubuntu.com/ubuntu](http://tr.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages



[http://docs.nvidia.com/cuda/cuda-installation-guide-linux/](http://docs.nvidia.com/cuda/cuda-installation-guide-linux/)

I try do run cuda. 
How will I make version correct ?

---

### Post by QIII on 2018-02-26
Threads merged.

---

### Post by papatya2 on 2018-02-26
gcc-5-base_5.3.1-14ubuntu2_amd64.deb

    Update the package index:

    # sudo apt-get update

    Install gcc-5-base deb package:

    # sudo apt-get install gcc-5-base

gcc-5-base is already the newest version (5.4.0-6ubuntu~16.04.9)
0 upgraded, 0 newly installed, 0 to remove...

---

### Post by monkeybrain20122 on 2018-02-27
It has nothing to do with gcc's version. 

Seems like you didn't install cuda properly with that dreaded .run file. You should have installed the .deb from [https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1604](https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1604) (choose network)

Here are my outputs

```
./mnistCUDNN
cudnnGetVersion() : 7005 , CUDNN_VERSION from cudnn.h : 7005 (7.0.5)
Host compiler version : GCC 5.4.0
There are 1 CUDA capable devices on your machine :
device 0 : sms 16  Capabilities 6.1, SmClock 1695.0 Mhz, MemSize (Mb) 8111, MemClock 4004.0 Mhz, Ecc=0, boardGroupID=0
Using device 0

Testing single precision
Loading image data/one_28x28.pgm
Performing forward propagation ...
Testing cudnnGetConvolutionForwardAlgorithm ...
Fastest algorithm is Algo 1
Testing cudnnFindConvolutionForwardAlgorithm ...
^^^^ CUDNN_STATUS_SUCCESS for Algo 0: 0.025152 time requiring 0 memory
^^^^ CUDNN_STATUS_SUCCESS for Algo 1: 0.030528 time requiring 3464 memory
^^^^ CUDNN_STATUS_SUCCESS for Algo 2: 0.041856 time requiring 57600 memory
^^^^ CUDNN_STATUS_SUCCESS for Algo 4: 0.074752 time requiring 207360 memory
^^^^ CUDNN_STATUS_SUCCESS for Algo 7: 0.095232 time requiring 2057744 memory
Resulting weights from Softmax:
0.0000000 0.9999399 0.0000000 0.0000000 0.0000561 0.0000000 0.0000012 0.0000017 0.0000010 0.0000000 
Loading image data/three_28x28.pgm
Performing forward propagation ...
Resulting weights from Softmax:
0.0000000 0.0000000 0.0000000 0.9999288 0.0000000 0.0000711 0.0000000 0.0000000 0.0000000 0.0000000 
Loading image data/five_28x28.pgm
Performing forward propagation ...
Resulting weights from Softmax:
0.0000000 0.0000008 0.0000000 0.0000002 0.0000000 0.9999820 0.0000154 0.0000000 0.0000012 0.0000006 

Result of classification: 1 3 5

Test passed!

Testing half precision (math in single precision)
Loading image data/one_28x28.pgm
Performing forward propagation ...
Testing cudnnGetConvolutionForwardAlgorithm ...
Fastest algorithm is Algo 1
Testing cudnnFindConvolutionForwardAlgorithm ...
^^^^ CUDNN_STATUS_SUCCESS for Algo 0: 0.027424 time requiring 0 memory
^^^^ CUDNN_STATUS_SUCCESS for Algo 1: 0.027552 time requiring 3464 memory
^^^^ CUDNN_STATUS_SUCCESS for Algo 2: 0.041632 time requiring 28800 memory
^^^^ CUDNN_STATUS_SUCCESS for Algo 4: 0.087040 time requiring 207360 memory
^^^^ CUDNN_STATUS_SUCCESS for Algo 7: 0.101376 time requiring 2057744 memory
Resulting weights from Softmax:
0.0000001 1.0000000 0.0000001 0.0000000 0.0000563 0.0000001 0.0000012 0.0000017 0.0000010 0.0000001 
Loading image data/three_28x28.pgm
Performing forward propagation ...
Resulting weights from Softmax:
0.0000000 0.0000000 0.0000000 1.0000000 0.0000000 0.0000714 0.0000000 0.0000000 0.0000000 0.0000000 
Loading image data/five_28x28.pgm
Performing forward propagation ...
Resulting weights from Softmax:
0.0000000 0.0000008 0.0000000 0.0000002 0.0000000 1.0000000 0.0000154 0.0000000 0.0000012 0.0000006 

Result of classification: 1 3 5

Test passed!
```

```
nvcc -V
nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2017 NVIDIA Corporation
Built on Fri_Nov__3_21:07:56_CDT_2017
Cuda compilation tools, release 9.1, V9.1.85

```
```

 nvidia-smi
Tue Feb 27 01:00:21 2018       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 390.30                 Driver Version: 390.30                    |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 1070    Off  | 00000000:01:00.0  On |                  N/A |
| N/A   48C    P0    36W /  N/A |    750MiB /  8111MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|    0      1215      G   /usr/lib/xorg/Xorg                           309MiB |
|    0      1831      G   compiz                                       239MiB |
|    0      6917      G   ...-token=921FAAD9C40D6F6503C4355B4D38C807    95MiB |
|    0     12140      G   ...-token=F2B0A2508EEA7E03D1418ACEA2F456F1   104MiB |
+-----------------------------------------------------------------------------+




```
 
Ubuntu 16.04.4, kernel 4.13.0-36


**Edited:** the Nvidia page you linked to that says cuda 9.1 is only compatible with gcc 5.3.1 is old, gcc 5.3.1 was the default gcc5 when Ubuntu 16.04 first release [https://packages.ubuntu.com/xenial/gcc](https://packages.ubuntu.com/xenial/gcc) and it was the newest for Ubuntu, that's why Nvidia put gcc 5.3.1, the Nvidia page obviously hasn't been updated since. You don't need to change gcc version, but just as general info, 5.3.1 is still in the repo, if you have synaptic you can see it easily by right clicking gcc5 > properties >version, then to downgrade to just have to highlight it, go to Package > force version to choose 5.3.1 and then pin it so it won't get upgraded. **BUT YOU SHOULD NOT DOWNGRADE**, this is just to show you it can be done easily.

---

### Post by monkeybrain20122 on 2018-02-27
BTW, if you have cuda 9.1 get tensorflow [here]("https://github.com/mind/wheels")

I tried pip3 install tensorflow-gpu, that installed tf but spewed a bunch of errors when imported, it appears that the pip version only supports cuda8 and earlier. The gpu version of both 1.5 and 1.41 from the link work on my machine (tested with python-2.7, 3.5 and 3.6),

---

### Post by papatya2 on 2018-02-27
I installed cuda again. I think cuda wasn't properly installed. I used .deb in link provided.
Updated some new files...
And then I installed nvidia 390.25 driver version for linux.
Then, it is running, Test pased, test is ok.

Thank you :o)
I will try tensorflow next step.

./mnistCUDNN
....
Test passed !

---

