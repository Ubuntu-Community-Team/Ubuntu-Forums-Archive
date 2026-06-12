---
title: "Ubuntu boots to a black screen"
date: 2012-12-20
forum: General Help
---

### Post by Rabark on 2012-12-20
**My Problem:**

When I boot to Ubuntu (12.04) through GRUB2 (Win XP / Ubuntu dual boot setup), I am presented with a black screen.  No desktop, no shell prompt, no messages, etc. . .just a black screen.

**How I got here:**

Being a gamer, I wanted to try out the Steam for Linux beta.  I installed the Steam beta client for Linux, and after logging into Steam it said my nVidia driver needed to be 304.22 or better.

So I installed the 304 driver through System Settings, and rebooted.  Logged back into Steam and it worked fine, but gave me a pop-up message saying that I should use the 310 driver for nVidia.

Installing the 310 driver gave me an error.  So I tried installing it again.  This time the install seemed to work.  The System Settings UI said it was installed and I needed to reboot.

I rebooted, and was presented with a black screen.  I powered off, and then rebooted again, this time into recovery mode.  I selected "continue booting normally", and was presented with a shell login prompt.  I logged in, and figuring that the 310 nVidia driver was the culprit I executed the following command:

```
sudo apt-get install nvidia-current
```

It installed successfully from what I could tell.  So I tried rebooting Ubuntu again, only to be presented with the same black screen.

Is there hope for me, or should I just reinstall Ubuntu from the live CD?

-Robert

---

### Post by oldfred on 2012-12-20
Installing nvdia-current reverted you back to the older version. To install the newer versions did you download directly from nVidia? 

From my 12.04 install.

```
fred@fred-Precise:~$ dpkg -l | grep -i nvidia*
rc  nvidia-173                             173.14.30-0ubuntu8                                  NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common                          1:0.2.44.2                                          Find obsolete NVIDIA drivers
rc  nvidia-current                         295.40-0ubuntu1                                     NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-current-updates                 304.43-0ubuntu0.1                                   NVIDIA binary Xorg driver, kernel module and VDPAU library
rc  nvidia-settings                        295.33-0ubuntu1                                     Tool of configuring the NVIDIA graphics driver
ii  nvidia-settings-updates                304.43-0ubuntu0.2                                   Tool of configuring the NVIDIA graphics driver

```

---

