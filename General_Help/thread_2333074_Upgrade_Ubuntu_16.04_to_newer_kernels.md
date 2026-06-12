---
title: "Upgrade Ubuntu 16.04 to newer kernels"
date: 2016-08-06
forum: General Help
---

### Post by courtney2 on 2016-08-06
Hi,

I need to get a kernel that is 4.5 or later to get support for a piece of hardware that I have. I know there's a way to grab kernel 4.6 for Ubuntu 16.04, but to my understanding I will have to manually update the kernel each time there is a new kernel released if I follow these instructions:

[http://ubuntuhandbook.org/index.php/2016/05/install-linux-kernel-4-6-ubuntu-16-04/](http://ubuntuhandbook.org/index.php/2016/05/install-linux-kernel-4-6-ubuntu-16-04/)

I would rather not do that and would like for apt to do that job for me. Is there a backport repo for Ubuntu that I can grab this kernel from or something like that?

---

### Post by jeremy31 on 2016-08-06
Why not just file a bug report?  Many times they will pull updates from newer kernels to support hardware if they know there is a problem.

There is a guide to filing bug reports [https://ubuntuforums.org/showthread.php?t=1011078](https://ubuntuforums.org/showthread.php?t=1011078)

What hardware are you needing support for?

---

### Post by courtney2 on 2016-08-07
Cool thanks! It's actually for PS4 controller DS4 controller. I know it got support with Linux kernel 3.18, but after doing some research I found that in newer controllers they made some changes. The changes for the new PS4 controllers were implemented in kernel 4.5 (so I have heard).

---

### Post by jeremy31 on 2016-08-07
What kernel are you using ```
uname -a
```

I was actually able to compile kernel source from linux-next with the 4.4.0-31 headers after reverting a couple of commits.  It might be worth a try if you don't have secure boot enabled just to see if the fix is out there

---

### Post by courtney2 on 2016-08-07
I am on 4.4.0-31 also. I could certainly grab kernel 4.6 which was built by ubuntu and made into a .deb. I always disable secure boot so won't be an issue. People with the same issue have said the fix is in 4.5, and I know the current 4.4.0-31 kernel in ubuntu doesn't support it because that's the kernel I am using right now

---

### Post by jeremy31 on 2016-08-07
Download the attachment and extract it to desktop.  Then we will make a backup of the current module
```
sudo cp /lib/modules/4.4.0-31-generic/kernel/drivers/hid/hid-sony.ko /lib/modules/4.4.0-31-generic/kernel/drivers/hid/hid-sony.ko.bak
```

Then we copy the new version
```
cd Desktop
sudo cp hid-sony.ko /lib/modules/4.4.0-31-generic/kernel/drivers/hid/hid-sony.ko
sudo depmod -a
```

reboot and see if it works

---

### Post by grahammechanical on 2016-08-07
Still under development 16.10 does not yet have kernel 4.5. So, I doubt that there will be any back porting to 16.04 until 16.10 moves off of kernel 4.4. and even then 16.04 most likely will not get the kernel in 16.10 until there is another 16.04 point release.

It looks like kernel 4.5 is going to be by-passed. Which is often the way.

[https://launchpad.net/~canonical-kernel-team/+archive/ubuntu/ppa](https://launchpad.net/~canonical-kernel-team/+archive/ubuntu/ppa)

[https://ubuntuforums.org/showthread.php?t=2326220](https://ubuntuforums.org/showthread.php?t=2326220)

[URL="https://ubuntuforums.org/showthread.php?t=2318508"]https://ubuntuforums.org/showthread.php?t=2318508

[/URL]Regards

---

### Post by courtney2 on 2016-08-08
Thank you for the information grahammechanical. Currently now though my controller started magically working and accepting input, but it is no longer recognizable via bluetooth, so my dilemma has sort of swapped

---

