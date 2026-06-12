---
title: "Installing 12.04.5 headless multiple GPU server/CUDA6.0 - 12.10 not supported anymore"
date: 2014-08-13
forum: General Help
---

### Post by danhansendenmark on 2014-08-13
Hi,


I've been running a few headless multiple GPU boinc servers on 12.10/CUDA5.5 because of the "bug" in the 12.04.4 update. [https://developer.nvidia.com/cuda-toolkit-55-archive](https://developer.nvidia.com/cuda-toolkit-55-archive) But, 12.10 is not supported any more. 
I noticed that there's no warning at CUDA6.0/Ubuntu 12.04.5 so I tried to build the system using these. Everything went pretty well until I got to this command (which worked fine in 12.10/CUDA5.5). Please help me edit or correct this command so that it can be done. Here's the command and the errors which appeared:

```

  # apt-get install linux-image-extra-$(uname -r) x11-xserver-utils mesa-utils

Reading package lists... Done
Building dependency tree
Reading state information... Done

E: Unable to locate package linux-image-extra-3.13.0-32-generic
E: Couldn't find any package by regex 'linux-image-extra-3.13.0-32-generic'


```

Here's a few additional commands I use, so that you can maybe get an idea of what I'm doing:

```


[...]

#19 # apt-get install linux-image-extra-$(uname -r) x11-xserver-utils mesa-utils   <----- errors because of this command 

#20 # modprobe nvidia

#21 # nvidia-xconfig --enable-all-gpus 

#22  cp /etc/X11/XF86Config /etc/X11/xorg.conf

[...]


```


I'm looking forward to hear you ;)


Kind Regards,
Dan Hansen/Denmark

---

### Post by ian-weisser on 2014-08-13
You seem to still be using a 14.04 kernel, not a 12.04 kernel.

And you're not up to date.

You are looking for 3.13.0-32, but the latest version for 14.04 is 3.13.0-34, pushed out today.
So -32, and it's associated extras, won't be in the repositories anymore.

---

### Post by danhansendenmark on 2014-08-14
Hi Ian,


Thanks my friend, for helping me ;)

As you can guess, I'm not quite the guru I wish to be, have only been "training in the the Ubuntu Gym" for 1.5 years ;)

It's  Ubuntu Server 12.04.5 and CUDA6.0, but a ToDo I made in march. It  worked with 12.10 and CUDA5.5. I'll show you my ToDo so that you can see  what it is that I'm doing.

```


Headless Ubuntu Server 12.10 64bit Multiple GPU Boinc Server:
SOLVED! 11.03.2014 Kl. 04:51am

[...]

# apt-get install build-essential linux-headers-`uname -r`
# wget http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1210/x86_64/cuda-repo-ubuntu1210_5.5-0_amd64.deb
# dpkg -i cuda-repo-ubuntu1210_5.5-0_amd64.deb
# apt-get update
# apt-get install cuda-5-5
# export CUDA_HOME=/usr/local/cuda-5.5
# export LD_LIBRARY_PATH=${CUDA_HOME}/lib64
# PATH=${CUDA_HOME}/bin:${PATH}
# export PATH

# reboot -h now
# apt-get install linux-image-extra-$(uname -r) x11-xserver-utils mesa-utils       <------ It's here I get the errors
# modprobe nvidia
# nvidia-xconfig --enable-all-gpus
# cp /etc/X11/XF86Config /etc/X11/xorg.conf

Install Boinc!


```


The ToDo changes the "stamp" or "version number" or what its called, or I think it does. 

```
# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:        12.04
Codename:       precise

```

```
# uname -a
Linux beaufort 3.13.0-32-generic #57~precise1-Ubuntu SMP Tue Jul 15 03:51:20 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

```
# cat /proc/version
Linux version 3.13.0-32-generic (buildd@phianna) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #57~precise1-Ubuntu SMP Tue Jul 15 03:51:20 UTC 2014

```

---

