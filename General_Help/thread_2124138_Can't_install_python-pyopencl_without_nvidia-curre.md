---
title: "Can't install python-pyopencl without nvidia-current??"
date: 2013-03-09
forum: General Help
---

### Post by w0ss4g3 on 2013-03-09
Hi, Using Ubuntu 12.04 (32 nbit). I've got an AMD card, running the 13.1 catalyst's, installed manually. This was the only way I could get my dual display to work.

I want to install the pyopencl library, but if I try "sudo apt-get install python-pyopencl", then I get:

The following extra packages will be installed:
  dkms libboost-python1.46.1 nvidia-current nvidia-settings python-opengl
Suggested packages:
  python3 libgle3
Recommended packages:
  nvidia-opencl-icd

Which forces me to install the nvidia driver. I can use the opencl library in python after this. However, as soon as I reboot, it breaks my video drivers and I have to remove everything and reinstall the AMD drivers.

Strangely, I also get nvidia-current coming up if I try to install the ubuntu-desktop package:

The following extra packages will be installed:
  nvidia-common
The following NEW packages will be installed
  nvidia-common ubuntu-desktop


I'm a bit perplexed here, why are these dependencies there?

Can anyone else?

Thanks in advance

---

