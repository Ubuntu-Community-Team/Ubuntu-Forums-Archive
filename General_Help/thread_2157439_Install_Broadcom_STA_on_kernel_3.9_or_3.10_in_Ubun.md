---
title: "Install Broadcom STA on kernel 3.9 or 3.10 in Ubuntu GNOME 13.04??"
date: 2013-06-25
forum: General Help
---

### Post by Roasted on 2013-06-25
Hello. I have been running Ubuntu 13.04 for some time now. Ever since then, I have been having hard lockups at random times. I posted a bug report here - [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1188774](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1188774) - but there hasn't been any substantial progression.

I have a Broadcom wireless card in this laptop, a Lenovo E430. Due to Lenovo being just such a joy to work with, I am unable to change my wireless card. Reasoning behind this is during boot, the system checks the hardware and makes sure it's signed. Putting an Intel wireless card in this laptop will result in a failure to boot. Good job, Lenovo. (facepalm)

I upgraded to kernel 3.9 earlier on, but I was unable to get my Broadcom STA driver working. As a result of 5 lockups yesterday alone, I am at a loss for how to work around this issue. The system has become so unpredictable that I cannot rely on it for work usage any longer. I am tempted to put in the alpha of Ubuntu GNOME 13.10 - no, I'm not kidding. But as a last ditch effort, I'd REALLY like to be using kernel 3.9, or even 3.10 if need be, in an order to see if the newer kernels fix the issues I'm having. But like I said, I cannot get my Broadcom STA working. 

If anybody can provide me with some insight on getting my Broadcom drivers installed on Ubuntu GNOME 13.04 in kernel 3.9 or 3.10, I'd be much appreciative. 

Thank you!

---

### Post by Roasted on 2013-06-26
So here's what I'm looking at. I basically want a distro that is capable of Gnome 3.8, whether natively or through an additional repo.

Fedora 19 - Releasing in a few days. Problem is my laptop requires the Windows 2012 parameter in the grub file for brightness to work. There's a current bug in F18/F19 that changes the space between Windows and 2012 to x20, so it renders as Windowsx202012, which is of course not a proper parameter. Waiting on that to get fixed.

openSUSE 12.3 - Awesome release, but I find it's impossible to truly love. I had to reinstall twice last night, once due to the Broadcom driver (go freakin figure) since once I installed it, it refused to boot, and the second time due to the 3.8 repo causing it to lock up on boot. No idea otherwise, but meh.

Debian - Likely won't get Gnome 3.8 before I retire.

Ubuntu GNOME 13.04 - Awesome due to the Gnome3 PPA, but Ubuntu GNOME 13.04 is currently on kernel 3.8. It seems as if there's a bug existent in kernel 3.8 that is giving me some grief. That's why I want to try out 3.9 but I cannot due to not having wireless capability. Likewise, I cannot switch my wireless card because Lenovo decided to be downright foolish and lock the system down to signed hardware only. Ubuntu 13.04 + 3.9 + wireless is ultimately the best bet.

Or, there's always Arch, which I'm about an hour away from installing if this Broadcom/3.9 bridge cannot be crossed.

---

