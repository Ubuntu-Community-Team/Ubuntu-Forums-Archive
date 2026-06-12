---
title: "No HDMI sound with latest kernel 3.19.0-18-generic"
date: 2015-05-23
forum: General Help
---

### Post by fprietog on 2015-05-23
Hello,

I'm using Ubuntu 15.04 64 bits (Desktop Edition). CPU Intel Core i7-4790, GPU Intel HD4600.

Problem: there is no HDMI out sound with latest kernel 3.19.0-18-generic. I'm sure it's a kernel problem because when I boot with previous kernel (3.19.0-16-generic) the HDMI sound works, but with the newest kernel it doesn't.

Here is an screenshot of the sound config under 3.19.0-16-generic. It shows the HDMI device, and it works:

[IMG]http://rt002nf0.eresmas.net/Temp/FPGLINUX%203.19.0-16-generic_01.jpg[/IMG]


Here is the same screenshot under the newest kernel 3.19.0-18-generic. No HDMI driver shown:

[IMG]http://rt002nf0.eresmas.net/Temp/FPGLINUX%203.19.0-18-generic_01.jpg[/IMG]



Here is more info using i-nex: with kernel 3.19.0-16-generic:

[IMG]http://rt002nf0.eresmas.net/Temp/FPGLINUX%203.19.0-16-generic_02.jpg[/IMG]

[IMG]http://rt002nf0.eresmas.net/Temp/FPGLINUX%203.19.0-16-generic_03.jpg[/IMG]


But with kernel 3.19.0-18-generic... nothing:
[IMG]http://rt002nf0.eresmas.net/Temp/FPGLINUX%203.19.0-18-generic_02.jpg[/IMG]


Please, if someone knows of to fix, or at least can point me where can I fill a bug to be checked and the info I need to provide, I'll be grateful.

I've tried to fill a bug in [https://bugs.launchpad.net/~canonical-kernel-team](https://bugs.launchpad.net/~canonical-kernel-team) but I'm not allowed to.


Thanks and best regards.

---

### Post by fprietog on 2015-05-23
I just found several similar bugs open: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1457369](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1457369)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1457446](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1457446)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1457697](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1457697)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1458196](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1458196)

---

