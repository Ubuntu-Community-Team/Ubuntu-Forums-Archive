---
title: "Is it possible to clone a dual boot?"
date: 2007-05-28
forum: General Help
---

### Post by the lemming on 2007-05-28
I have tried to clone XP along with another operating system using Norton Ghost 2003 but I have never been successful at this.

I can happily clone one operating system which is XP and this ability has got me out of a shed load of problems when either trying to dual boot Vista or any number of Linux Distros.

However when I clone two systems and then try to re-clone the entire drive I get error messages and, from what I can gather, an unusable computer.  I then have two options.  The first is to re-clone for one operating system or Boot up my computer with a Window's 98 boot disk and type" fdisk/mbr".  I have no idea what this command does but it does get my windows operating system up and running.  Unfortunately it some how wipes out the other operating system.  Which is a bit of a bugger.

Anybody else had similar problems?
And if so, how did you solve this little problem?


Cheers

---

### Post by aysiu on 2007-05-28
I don't know that it's possible to clone a dual boot.

Is the target computer exactly the same specifications? It would have to be for the cloning to work, anyway.

---

### Post by the lemming on 2007-05-31
> **aysiu said:**
> I don't know that it's possible to clone a dual boot.

Is the target computer exactly the same specifications? It would have to be for the cloning to work, anyway.


It is for backing up my master hard drive in case it ever dies and I lose XP which was installed on it when I bought the computer.

---

### Post by the lemming on 2007-06-01
> **aysiu said:**
> I don't know that it's possible to clone a dual boot.

Is the target computer exactly the same specifications? It would have to be for the cloning to work, anyway.

I think that I have solved the problem with the following link

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

However I'm at work and can't confirm this till I get home but I'm going to give it a try and see what happens

---

### Post by rillip on 2007-06-01
I don't know anything about the cloning, however, the fixmbr command overwrites your MBR (master boot record) with Window's booter instead of Grub.  To get to your Linux system again, there are a number of options, the easiest probably being to boot up a live CD and install Grub, letting it overwrite the mbr again.  It is possible as well to install it to a different location and load from there as well.

---

