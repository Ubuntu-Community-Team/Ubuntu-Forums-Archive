---
title: "Distorted display"
date: 2015-07-30
forum: General Help
---

### Post by Krzym on 2015-07-30
Hi,
I wanted to install Ubuntu on few PCs, but one of them got strange problem.

The display is distorted, like realy low res or missig pixels? It's hard to explain for me.
[http://1drv.ms/1JKHr6M](http://1drv.ms/1JKHr6M)
[http://1drv.ms/1MU9GTu](http://1drv.ms/1MU9GTu)

On other PC ubuntu starts on 2 monitors with no problem (I checked 4PCs, only one don;t work)
And the broken one got strange restart flickering <- like in movie attached

[HTML]ubuntu@ubuntu:~$ lspci -k | grep -EA2 'VGA|3D' 01:00.0 VGA compatible controller: NVIDIA Corporation GK104 [GeForce GTX 660 Ti] (rev a1)     Subsystem: ASUSTeK Computer Inc. Device 841f 01:00.1 Audio device: NVIDIA Corporation GK104 HDMI Audio Controller (rev a1) ubuntu@ubuntu:~$[/HTML]

I checked 32 and 64 bit, preinstalled and preveiw mode.
Now I got only preview mode, and I need to fix this issue before installation if possible. 


Hope you can find a solution.
Best regards,
K.

---

### Post by grahammechanical on 2015-07-30
What is the difference? Do all four machines have the same video adapter?

According to the Nvidia web site the oldest driver for the Nvidia GTX660 Ti is driver 346.47 released on 24th February 2015. The newest driver available is driver 352.30 released on 28th July 2015. There are other drivers released in between those two dates.

What version of Ubuntu are you using? Versions of Ubuntu older than the video adapter are unlikely to have the correct video drivers. When you install do not tick the box Install third party software. Then you will not get a proprietary video driver but the default open source video driver (Nouveau) which may be sufficient to get Ubuntu installed. Then you can use Software & Updates>Additional Drivers tab to see if a suitable proprietary video driver is available.

But you do need the latest version of Ubuntu. You may need to install Ubuntu 15.04 even though it only has support until January 2016 in order to get the very latest proprietary drivers in the 15.04 repositories.

Regards.

---

### Post by Krzym on 2015-07-31
I downloaded Ubuntu last week so I think I got the lastest one.
Other 3 PC are almost the same, 2 are 660Ti, 1 is 660.

It is almost impossible to install Ubuntu on this PC and then look for some fix. Maybe the photo do not show that, but screen is almost unreadable (you need to shake window left to right to see anything).

---

### Post by K3N8 on 2016-01-30
I got exactly the same thing on a older Pentium machine runnen 32-bit version of Ubuntu 14.04. Has anybody found a solotion?

---

