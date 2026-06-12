---
title: "Reinstalling nvidia binary due to kernel update"
date: 2007-02-10
forum: General Help
---

### Post by darweth on 2007-02-10
Hi... I am coming to you LIVE from a live disc!!

uhhh... sorry.  anyway, i am fully aware updating the kernel will break my x-serv or whatever.  the problem is how do i get to a working command-line prompt now?  i reboot my computer and it tells me X/xorg/etc is messed up and would I like to look at stuff.  I said, "Hell no... take me to the prompt so I can cd Desktop and sudo sh NVIDIA-Linux-x86-1.0-9631-pkg1.run" but it does not comply.  Instead I get dumped to a completely blank black screen that I can type on but nothing happens.  There is nothing showing me my directory, blah blah.  Help!

I also tried recovery, but it said could not open file.  I suppose recovery mode doesn't allow to run certain system changing stuff?  Should I try it again?

One more thing: I had both the new AND old kernel in grub menu.  Is this normal?  Will the old one ever disappear?

Thanks

Basically I just want to know how to get to a working shell!!!!

---

### Post by Ossipon on 2007-02-10
if x does not work pressing crtl+alt+F1 should give you a commandline; but recovery mode should also work. It should allow you to change anything you want.

The old kernel will stay in the grub menu. You can also still boot it and it will disappear if you remove the kernel image

---

### Post by darweth on 2007-02-10
Well, I am logged into the OLD kernel right now with nvidia/beryl etc working fine.

Here is what happens when I go into Recovery with the NEW kernel and try to update nvidia...
```

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
```

for this... it says all packages are not installed so not removed... init.d/NVIDIA doesn't exist... etc
```
sudo sh NVIDIA-Linux-x86-1.0-9631-pkg1.run
```

for this it says cannot open this file

---

### Post by darweth on 2007-02-10
I am going to try to do the base steps from the old kernel and that is not working out either --- CHECK IT


```
bepogi@bepogi-desktop:~$ sudo apt-get install --reinstall linux-restricted-modules-`2.6.17-11-386` nvidia-glx
bash: 2.6.17-11-386: command not found
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-restricted-modules
bepogi@bepogi-desktop:~$ 

```

---

### Post by hotani on 2007-02-10
got the same thing. I'm running the old *-10-generic kernel since 11 boned my x server because of nvidia.

---

### Post by darweth on 2007-02-10
```
bepogi@bepogi-desktop:~$ sudo apt-get install linux-headers-`2.6.17-11-386` build-essential gcc gcc-3.4 xserver-xorg-dev
bash: 2.6.17-11-386: command not found
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is not installed, so not removed
build-essential is already the newest version.
gcc is already the newest version.
gcc-3.4 is already the newest version.
xserver-xorg-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bepogi@bepogi-desktop:~$ sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx is not installed, so not removed
Package nvidia-settings is not installed, so not removed
Package nvidia-kernel-common is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

more info... i guess it is a good thing up to there (except for maybe linux-headers... not installing??), but then installing nvidia itself with sudo sh NVIDIA-blahblahblah does not work in recovery... I am stumped.

---

### Post by darweth on 2007-02-10
Any ideas at all?  I would try Envy, but I must use 9631 instead of the latest Nvidia due to having an older unsupported card (Geforce 4MX).  I am sure the answer is simple and under my nose!  :/

---

