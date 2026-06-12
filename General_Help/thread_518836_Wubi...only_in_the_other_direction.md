---
title: "Wubi...only in the other direction"
date: 2007-08-06
forum: General Help
---

### Post by rockin_goliath on 2007-08-06
Wubi is a really cool idea for installing Ubuntu from within a Windows machine. As I was thinking about it, it occurred to me that the concept of installing an OS to a virtual disk is probably the same way that Boot Camp works in Mac OS X. My only problem is that in the case of Wubi and Boot Camp, Windows/Mac OS X is the primary OS, and not Ubuntu. Would it be possible to make an installer similar to Wubi, only it installed Windows to a virtual disk from within Ubuntu, and then added an entry to Grub? That way we could enjoy the benefits of an easy, no-partitioning-necessary dual boot setup and still maintain Ubuntu as the primary OS, thus being able to remove Windows whenever we felt like it.

Now, I'm not a programmer, just a dude with ideas. What does everyone think?

---

### Post by tuxcantfly on 2007-08-06
> Now, I'm not a programmer, just a dude with ideas. What does everyone think?

Not possible; Windows and Mac OSX are not open-source, so we can't modify the boot process to let them boot off a loopmounted filesystem (and even if you managed to hack through it to get it to work, redistributing your modified versions would be illegal), and also, they don't natively support ext3 or any of the other popular Linux filesystems. Ah yes, the wonders of proprietary software.

---

### Post by tuxcantfly on 2007-08-06
Then again, though, you could always use a virtual machine like QEMU or VMware, only you'll have to boot up one operating system before you can launch the other.

---

### Post by ago on 2007-08-07
A good approach is to use Linux for everything and set up a seamless virtualization ([https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization) ) for the few apps that you miss. It takes a little bit to setup but the process should be streamlined already in ubuntu 7.10. That works for everything that does not require 3D access. For 3D access [http://www.wine-doors.org](http://www.wine-doors.org) might do the trick in some cases. As tux said it is not really possible to do a wubi-like approach for windows since that would require a modification of the boot process and there is no access to the code. That is why open source is superior...

---

### Post by rockin_goliath on 2007-08-07
Thanks for the info Tuxcanfly. I am not a gamer, so I don't need access to 3D/Direct X support, I was just asking on behalf of the people who do. I mean, another way to basically acomplish the same dual boot task is to resize the Ubuntu partition to make room for a Windows installation, and somehow preserve Grub or make it easier to restore once Windows destroys it. It's been suggested a couple of times, but I'm not sure what the status is.

---

