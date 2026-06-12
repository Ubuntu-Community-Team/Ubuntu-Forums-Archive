---
title: "VirtualBox on Ubuntu and PCLinuxOS"
date: 2007-04-04
forum: General Help
---

### Post by ChameleonDave on 2007-04-04
I have installed [VirtualBox]("http://en.wikipedia.org/wiki/VirtualBox") on two distros.

The PCLinuxOS repository have version 1.3.6, so I installed that.  Ubuntu Edgy's repository didn't have it, so I downloaded the latest version (1.3.8) from [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads).

I created an image and installed Windows XP on it.  It worked very well, and I was impressed with the speed of the virtual system, especially compared to the sluggishness that I have experienced with [QEMU]("http://en.wikipedia.org/wiki/QEMU").

But I have encountered a strange problem.  On PCLinuxOS, the virtual machine connects to the internet but fails to make a network share with my files on my hard-drive.  On Ubuntu, *vice versa*.

What could be the problem?  What can I change on PCLinuxOS so that it finds my files, and what can I change on Ubuntu so that it connects to the internet?

---

### Post by Recked on 2007-04-04
Hello,

Not able to help with your issue as I am not able to even get XP installed. How exactly do I create an image of my XP disk if you don't mind my asking? I have a disk supplied by Dell to reinstall XP with Service Pack 2 on it. It seems no matter what disk I put in the cd drive (XP or another linux distro) I get an error from VirtualBox about can't find bootable disk or something similar.

Did you have this issue when you first started?

Thank you

---

### Post by ChameleonDave on 2007-04-04
> **Recked said:**
> Hello,

Not able to help with your issue as I am not able to even get XP installed. How exactly do I create an image of my XP disk if you don't mind my asking? I have a disk supplied by Dell to reinstall XP with Service Pack 2 on it. It seems no matter what disk I put in the cd drive (XP or another linux distro) I get an error from VirtualBox about can't find bootable disk or something similar.

Did you have this issue when you first started?

Thank you
I had no problems with that.  I clicked "new" in the program and followed the wizard to create a blank image.  Then I booted into it, making sure that the XP CD was in the CD tray, and that it was mounted in the virtual machine.

Did you do that?  If you still have trouble, read the PDF manual on the official site.

---

### Post by Recked on 2007-04-04
Hi,

I got XP installed just fine and everything appears to work except one small but rather important item which is that the whole keyboard works when using basic apps within Windows but when I go to activate XP via the internet I lose the number 1 and 5 keys both on the upper portion of the keyboard and also the keypad to the side. I also loose a few letters like U and R etc. I check all the keys from within Wordpad and they all work but for activation they don't so I guess I am forced to call.

thanks

---

### Post by ChameleonDave on 2007-04-05
That's bizarre.  But if it only happens when activating XP, then just don't activate XP.

---

### Post by Recked on 2007-04-06
Hey Dave,

That's fine except after 30 days XP will not longer boot at all from what I understand no???

Thanks

---

### Post by ChameleonDave on 2007-04-08
> **Recked said:**
> Hey Dave,

That's fine except after 30 days XP will not longer boot at all from what I understand no???

Thanks
First I've heard of it!

I have never registered XP.  When it asks you to, it says it's optional, and I have never had any problems with it refusing to boot for such reasons.

---

### Post by ChameleonDave on 2007-04-09
Update:

I have solved the file-sharing problem in PCLinuxOS by upgrading to the latest version of VirtualBox (the version in the PCLinuxOS repos was stripped of file-sharing capabilities).

However, on Ubuntu I am still getting no internet.

---

