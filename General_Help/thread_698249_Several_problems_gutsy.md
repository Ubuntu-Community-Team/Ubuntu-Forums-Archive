---
title: "Several problems gutsy"
date: 2008-02-16
forum: General Help
---

### Post by jay3712 on 2008-02-16
Ok my Gutsy install has recently taken a huge dump on me, and I think it may be b/c I upgraded to the 2.6.24 kernel, but I'm really not sure. Here are my symptoms:
- iPod will not be recognized in Amarok, [here]("http://ubuntuforums.org/showthread.php?t=695027") is my other thread.
- Other USB devices such as flash memory and usb keys have quit working, but my logitech USB mouse still works perfectly.
- Java in Firefox 3 quit working.
- I booted from my previous gutsy kernel but then I have no wireless ability.
- I ran this while booted into my 2.6.22-14 kernel:
	```
jason@jason-laptop:~$ sudo apt-get remove linux-image-2.6.24-5-generic linux-headers-2.6.24-5-generic linux-headers-2.6.24-5 linux-restricted-modules-2.6.24-5-generic linux-ubuntu-modules-2.6.24-5-generic
[sudo] password for jason:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-image-2.6.24-5-generic
```
which is from the [easy kernel upgrade]("http://ubuntuforums.org/showthread.php?t=646755") thread. 
What info should I post?
First I want to roll back to the gutsy kernel (with working wireless networking). It was obviously a mistake to upgrade to the Hardy kernel. Then hopefully this will resolve some of my problems and then I can get everything else working like it should.

---

### Post by Anduu on 2008-02-16
Try re-enabling the Hardy repos like you did from the how-to and then try removing the 2.6.24 kernels.Disable  the the Hardy repos and reinstall the 2.6.22 kernel.

---

