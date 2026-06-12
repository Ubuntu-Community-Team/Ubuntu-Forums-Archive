---
title: "Nvidia can't find kernel source"
date: 2013-09-18
forum: General Help
---

### Post by josephellengar2 on 2013-09-18
Hello. I know this question has already been asked, but none of the existing answers work for me. I've tried just about everything I can find.

Anyway, I'm using Ubuntu 12.04 x64 and kernel 3.2.0-53. I am trying to install the nvidia driver, but running into some rather irritating errors. Every time I try to install I get the following:

```

Module build for the currently running kernel was
skipped since the kernel source for this kernel
does not seem to be installed.

```

My jockey.log file says the same thing. (Specifics vary based on what version of the driver I'm trying to install)
```

2013-09-18 23:08:48,452 WARNING: modinfo for module nvidia_319 failed: ERROR: modinfo: could not find module nvidia_319

2013-09-18 23:08:48,452 WARNING: /sys/module/nvidia_319/drivers does not exist, cannot rebind nvidia_319 driver
2013-09-18 23:08:05,937 DEBUG: Shutting down

```


I know what it's looking for, and the community consensus is that installing the headers should be enough. I have the headers installed for all of my installed kernels. I always keep the last two kernels installed just in case and the headers for both installed. I have double-checked and they are there. The linux-source package specifically says that it is not for 3rd party modules, although I did install it just in case and that didn't help. I have build-essential and related packages installed. 

For sources of the driver I have tried:
1) Installing nvidia-common from the repos and various specific versions
2) Installing the packages using the jockey gui
3) Using the ubuntu-x-swat ppa
4) Downloading and installing manually from Nvidia

So the problem is that the package can't find my headers. Where are the headers installed to? Is there a way that I can explicitly tell it to "look for headers here"? Is there another way to get this installed? This is just mystifying me.

Thanks!

---

### Post by sudodus on 2013-09-19
I know jockey is being phased out, but I don't remember in which version of Ubuntu. Maybe you have better luck, if you try to install the nvidia driver without jockey (using apt-get or Synaptic or some other front end for that purpose).

---

### Post by josephellengar2 on 2013-09-19
> **sudodus said:**
> I know jockey is being phased out, but I don't remember in which version of Ubuntu. Maybe you have better luck, if you try to install the nvidia driver without jockey (using apt-get or Synaptic or some other front end for that purpose).

Tried that already; didn't work. Right now I'm going to try to upgrade to 12.10 after backing up and see if the new version has better luck. I don't like to do that because I hate the 6-month cadence, but 14.04 will be an LTS, so it shouldn't be too bad.

---

### Post by sudodus on 2013-09-20
Are you trying to install the graphics driver, when the graphics is switched off, or inside a graphics desktop environment?

It might work better if you start at text screen with ***ctrl + alt + F2*** and from there run

```
sudo service lightdm stop
```

to stop the graphics. And then try again to install your nvidia driver. If still no go, try with another version of the nvidia graphics driver! Start trying with the ones available in the repositories (available with apt-get or Synaptic).

---

