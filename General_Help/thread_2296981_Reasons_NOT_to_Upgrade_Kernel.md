---
title: "Reasons NOT to Upgrade Kernel"
date: 2015-09-30
forum: General Help
---

### Post by speartip on 2015-09-30
I recently upgraded the Kernel on my Xubuntu 14.04 system to 4.1.9 LTS from here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.1.9-unstable/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.1.9-unstable/)
Mainly for the hell of it, & also to stick with the latest LTS Kernel.
I have to say that my system "appears" to run extremely well on it, probably snappier & smoother than the pre-installed 3.19 kernel.
Is there any dangers in doing this? Or any reason not to?

---

### Post by dino99 on 2015-09-30
the danger to drive in the wild (unstable packages) comes when you are not able to understand what goes wrong and then taking your own decision to fix the issue ;)
About new kernel(s) it can happen some trouble: abi mismach, graphic driver issue, ....
but if you have at least one other working kernel (more is not necessary & waste hdd space) installed, then you have a second choice to boot with, in case the latest installed kernel give you headaches

---

### Post by mastablasta on 2015-09-30
also you have stable kernels and development kernels. and I think these are stable. in case of hardware enablement stack they are kernels form releases between Ubuntu LTS editions

---

### Post by grahammechanical on 2015-09-30
As with many things, it all depends ...

A few months ago I decided that I would test release candidate kernels just for the hell of it. In particular it was kernel 4.0 series.

It turns out that the newest kernels often require newer proprietary video drivers. That is a problem that can easily be fixed. But in my case the newer proprietary video driver no longer supported my old video adapter. Therefore, the video driver kernel module would not compile. And the older proprietary video drivers in Additional Drivers did not run well with the latest kernels. And neither did the open source video driver. End of experiment.

I was doing this on the development version of 15.10 (wily werewolf). And now a few weeks later I have 2 installs of 15.10. One has kernel 4.0 and it runs well with the legacy proprietary video driver in Additional Drivers. And the other has kernel 4.2 running with the open source video driver. All courtesy of the Ubuntu kernel team. Everything comes to those who wait and who also upgrade to the next Ubuntu version or LTS point release.

So, as I said previously. It all depends. Best to experiment on another install of Ubuntu first before upgrading your daily working install of Ubuntu.

Oh, you might like to follow threads like this on in the Ubuntu Development Version section of this forum

[http://ubuntuforums.org/showthread.php?t=2294800](http://ubuntuforums.org/showthread.php?t=2294800)

Regards.

---

### Post by speartip on 2015-09-30
Thanks for all your replies.
All my hardware seems to run fine on this kernel, & being an LTS kernel I would suggest it should be stable.
I will run my system on this for a few days, to see if I hit any issues, as it does appear to run better.
I have kept the 3.19 stock kernel if the worst should happen. but so far so good.

---

### Post by Ralph L on 2015-09-30
After reading this I have a question:  I am running xubuntu 14.04 with the latest updates (as of 3 days ago).  If I run "uname -r" it says that I have 3.16.0-50-generic.  Yet, the OP of this thread says that he has a stock kernel of 3.19.  When I install the latest updates to 14.04, why don't I get the later stock kernel 3.19?  One of my computers requires 3.19 to run correctly and I would like to get a stock release for it.

Thanks for any info you can give me.

---

### Post by mastablasta on 2015-10-01
> **Ralph L said:**
> After reading this I have a question:  I am running xubuntu 14.04 with the latest updates (as of 3 days ago).  If I run "uname -r" it says that I have 3.16.0-50-generic.  Yet, the OP of this thread says that he has a stock kernel of 3.19.  When I install the latest updates to 14.04, why don't I get the later stock kernel 3.19?  One of my computers requires 3.19 to run correctly and I would like to get a stock release for it.

Thanks for any info you can give me.

you need to specifically install higher kernel or it would also be updates if you installed 14.04.2

read more here: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

in short this stack enables the LTS release to be (more) compatible with newer hardware.

---

