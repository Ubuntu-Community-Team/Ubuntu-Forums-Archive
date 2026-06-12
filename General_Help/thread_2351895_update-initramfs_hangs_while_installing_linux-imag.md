---
title: "update-initramfs hangs while installing linux-image-4.4.0-62-generic"
date: 2017-02-07
forum: General Help
---

### Post by arcus3 on 2017-02-07
I am running 16.04 LTS

an apt-get upgrade recently attempted to install linux-image-4.4.0-62-generic.  it got to update-initramfs for this kernel, which then hung. 

I've tried running update-initramfs by hand with the -v option, and it gets up to this point: 

Building cpio /boot/initrd.img-4.4.0-62-generic.new initramfs
I left it for several hours, and it really seems stuck.  The size of initrd.im-4.4.0-62-generic doesn't increase.  The size varies but tends to be around the 18M mark. 

(initrd.img-4.4.0-59-generic is 39M)

I've tried purging the linux kernel packages and reinstalling but it always gets stuck. 

dpkg --configure -a 

similarly gets stuck at the same point. 

df reports /boot at 86% capacity (32M free) so it's not that I've run out of space. 

I don't know what to do now, so... help! 

(II'm a little worried I'm going to end up with an unbootable system out of this...) 

thanks, 

--
-arc

---

### Post by tbenst on 2017-02-23
Same problem exactly. 59 is ok, 62+ having issues. Any luck in resolving? I'm afraid to reboot

---

### Post by mesiu842 on 2017-03-09
> **tbenst said:**
> Same problem exactly. 59 is ok, 62+ having issues. Any luck in resolving? I'm afraid to reboot

This is not only for 62+ I've 62 and 64 fully installed without problems. 64 was installed something about a week or 2 weeks ago. Yesterday I've tried to install 66 and then the problem appeared for me.
Looks like some bug:
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1667512](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1667512)

---

