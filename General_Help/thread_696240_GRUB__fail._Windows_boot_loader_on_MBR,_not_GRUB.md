---
title: "GRUB_ fail. Windows boot loader on MBR, not GRUB"
date: 2008-02-13
forum: General Help
---

### Post by TerrorAndHubris on 2008-02-13
So, I've updated Ubuntu 7.10 today on my Dell Inspiron E1505 and (I'm assuming) GRUB has been compromised. Now, I've read up on how to reinstall GRUB and get my system back, but the difference here is that I've got the Windows boot loader running the show first so that Windows (which I need to have) doesn't get touched. My question to you is: _how does this change things so that GRUB doesn't take over the MBR, or do I not have to worry as long as I specify the correct partition?_

Thank you kindly, in advance.

---

### Post by froy02 on 2008-02-13
You should not have to worry if grub installs in your MBR.  Messing the MBR does not neccesarily mess up your partitions.  As long as your partitions are intact your OS' and data is fine.
When you install Ubuntu and then boots into it for the first time, copy your menu.lst found in /boot/grub directory because when update the first time the kernel sometimes changes the menu.lst and forgets about window$, that is if you moved window$ up as the default to boot.

But if you still want to put grub somewhere else, on floppy, CD or separate boot partition, here's a good tutorial website for all that.
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

I use a separate partition for my menu.lst only because 1 of my computers has XP, Ubuntu i386, Ubuntu AMD64, and Ubuntu Hardy-Alpha.

You can also use Window$ boot.ini to boot in Window$ and Ubuntu but that would go into a Window$ forum.

---

### Post by TerrorAndHubris on 2008-02-13
I've already got the MBR working, its just that GRUB seems to have been corrupted.

Diagram:
PwrOn -> Windows Boot Loader -> Windows
                                                '--> GRUB -> Ubuntu

PwrOn - works
Windows Boot Loader - works
Windows - works
GRUB - FAILURE
Ubuntu - works? intact as far as I can tell

My worry is that "fixing" GRUB will overwrite the MBR thats already set.

And, as an update; I booted using a LiveCD of Ubuntu, opened up terminal and used the following:

sudo grub
find /boot/grub/stage1    !-- identified hd0,4
root (hd0,4)
setup (hd0,4)
quit
sudo shutdown -r now

only to accomplish absolutely nothing.

---

### Post by froy02 on 2008-02-18
> **TerrorAndHubris said:**
> I've already got the MBR working, its just that GRUB seems to have been corrupted.

Diagram:
PwrOn -> Windows Boot Loader -> Windows
                                                '--> GRUB -> Ubuntu

PwrOn - works
Windows Boot Loader - works
Windows - works
GRUB - FAILURE
Ubuntu - works? intact as far as I can tell

My worry is that "fixing" GRUB will overwrite the MBR thats already set.

And, as an update; I booted using a LiveCD of Ubuntu, opened up terminal and used the following:

sudo grub
find /boot/grub/stage1    !-- identified hd0,4
root (hd0,4)
setup (hd0,4)
quit
sudo shutdown -r now

only to accomplish absolutely nothing.

The setup code should be 'setup (hd0)' not 'setup (hd0,4)'.

---

### Post by TerrorAndHubris on 2008-02-25
Wouldn't "setup (hd0)" overwrite my mbr with grub? I want to avoid that at all costs... grub was fine being installed on the hd0,4 partition before.

---

### Post by froy02 on 2008-02-25
Yes, that would overwrite your mbr with grub. I misunderstood what you were trying to do.
Since you have grub installed in the Linux partition you need to edit your window$ boot.ini file to multi-boot.  I am not familiar with the procedure anymore but if you google boot.ini you should find the procedure easily.  I haven't been messing with window$ for a while now.

---

