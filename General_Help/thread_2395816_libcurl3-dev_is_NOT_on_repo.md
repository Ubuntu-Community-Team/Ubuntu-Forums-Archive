---
title: "libcurl3-dev is NOT on repo"
date: 2018-07-07
forum: General Help
---

### Post by satimis on 2018-07-07
Hi all,

I'm following below document to install Tensorflow on Ubuntu 18.04 
Ubuntu-18.04 Install Nvidia driver and CUDA and CUDNN and build Tensorflow for gpu
[https://github.com/nathtest/Tutorial-Ubuntu-18.04-Install-Nvidia-driver-and-CUDA-and-CUDNN-and-build-Tensorflow-for-gpu](https://github.com/nathtest/Tutorial-Ubuntu-18.04-Install-Nvidia-driver-and-CUDA-and-CUDNN-and-build-Tensorflow-for-gpu)

and couldn't find libcurl3-dev on repo

$ apt-cache search libcurl3-dev```

libcurl4-openssl-dev - development files and documentation for libcurl (OpenSSL flavour)

```

Whether I should install "libcurl4-openssl-dev" instead?

Thanks

Regards
satimis

---

### Post by nathtest on 2018-07-09
Hi ,

According to that post [https://askubuntu.com/questions/469360/what-is-the-difference-between-libcurl3-and-libcurl4](https://askubuntu.com/questions/469360/what-is-the-difference-between-libcurl3-and-libcurl4) using libcurl4-openssl-dev should be ok.
Let me know if that solved your issue so i can update the github.

Thanks.

---

