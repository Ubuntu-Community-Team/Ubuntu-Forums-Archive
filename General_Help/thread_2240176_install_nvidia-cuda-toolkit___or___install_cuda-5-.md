---
title: "install nvidia-cuda-toolkit   or   install cuda-5-5 / 6-0 ????"
date: 2014-08-18
forum: General Help
---

### Post by danhansendenmark on 2014-08-18
Hi,


I found this in here and wanted to ask the guru's of this forum:

```
[INDENT]  Quick and easy solution that worked for me (cuda 5.5, Lubuntu 14.04   64-bit):

  Make sure you're using nvidia's propietary driver (331.38 for me) from Start menu-> Preferences->Software & Updates.
      Download the .deb package for ubuntu 13.04 from Nvidia's site.
      Add repo
  sudo dpkg -i cuda-repo-ubuntu1304_6.0-37_amd64.deb

  sudo apt-get update
      Get dependencies
  sudo apt-get install freeglut3-dev build-essential libx11-dev libxmu-dev libxi-dev libgl1-mesa-glx libglu1-mesa libglu1-mesa-dev
      Get the toolkit
  sudo apt-get install nvidia-cuda-toolkit
      (Optional) Get nsight IDE
  sudo apt-get install nvidia-nsight
      And you're ready to go*

[/INDENT]

```[INDENT] 

[/INDENT]
Can't I  use the "apt-get install cuda-5-5" or "apt-get install cuda-6-0" since  it's this you "dpkg" ???? 

  After installing the toolkit using the command "apt-get install  nvidia-cuda-toolkit" I can't even find the directory under  "/usr/local/cudaxxx" !?!?
  
I'm building a headless multiple GPU boinc  system and so far I got it to work using 12.10. I would have used 12.04,  but since the 12.04.4 update, the CUDA 5.5 .deb package didn't work any more as you know. Therefore I found a different solution. Since the support  for 12.10 stopped my life has been "not so funny" because I simply  can't find a way to make it work again. I've tried every version since 12.04.4, I tried 12.10 as written before. Tried 13.10 and 13.04. I tried 14.04 and all of with both CUDA5.5 and CUDA6.0. Nothing works. I really don't want to wait for the .deb package for 14.04 to get on with my crunching and believe me, .run files will not work either !!! I've been working this issue for more than 9 month. Yes, I know... Some would solve this issue in a heartbeat, but I'm still learning. And I believe the best way to learn is to try, and then try again ;) Well, Try until it's stupid not to ask people who might know ;)

I hope you can help me. Below I'm posting my ToDo. It might just show you exactly what it is that I'm trying.
I know I'm not that great at explaining these hardcore issues ;)

My ToDo. Once it worked using Ubuntu Server 12.10/CUDA5.5 .deb package - But I can't find a new combination/version without getting problems. Here I tried to fit it to work using the 14.04 Server edition and the 13.04 .deb package as the ToDo from in here suggested. I know most of these examples is done with the Desktop version, but I hope you can help me anyroad ;)

```

# apt-get install build-essential linux-headers-`uname -r`
# wget http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1304/x86_64/cuda-repo-ubuntu1304_6.0-37_amd64.deb
# dpkg -i cuda-repo-ubuntu1304_6.0-37_amd64.deb
# apt-get update
# apt-get install cuda-5-5  <----- NO CAN DO !!! AND INSTALLING THE NVIDIA-CUDA-TOOLKIT DIDN'T WORK

# export CUDA_HOME=/usr/local/cuda-6.0
# export LD_LIBRARY_PATH=${CUDA_HOME}/lib64
# PATH=${CUDA_HOME}/bin:${PATH}
# export PATH

# reboot -h now
# apt-get install linux-image-extra-$(uname -r) x11-xserver-utils mesa-utils  
# modprobe nvidia
# nvidia-xconfig --enable-all-gpus
# cp /etc/X11/XF86Config /etc/X11/xorg.conf

```



Kind Regards, 
Dan Hansen/Denmark

---

