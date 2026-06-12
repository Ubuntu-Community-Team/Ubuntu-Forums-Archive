---
title: "Booting Dual Hard Drives"
date: 2008-03-10
forum: General Help
---

### Post by jmorth on 2008-03-10
Here's the deal.

My current box has two hard drives: one IDE drive with ubuntu 7.10 and one SATA for storage of music and the like.

I went and bought another IDE hard drive for a different computer of mine that I was going to use as a Windows box.

Then I got the bright Idea to just install it in my current box.

My question is: Is there a way to have a boot loader give me the option to pick the windows install on the slave drive at start up? If there is, how?

I appreciate any help.

---

### Post by marufaberlin on 2008-03-10
Sure thing, do you use lilo or grub? What do you mean about the windows install, doo you mean the windows installation or the windows installer?

---

### Post by sandysandy on 2008-03-10
> **jmorth said:**
> Here's the deal.

My current box has two hard drives: one IDE drive with ubuntu 7.10 and one SATA for storage of music and the like.

I went and bought another IDE hard drive for a different computer of mine that I was going to use as a Windows box.

Then I got the bright Idea to just install it in my current box.

My question is: Is there a way to have a boot loader give me the option to pick the windows install on the slave drive at start up? If there is, how?

I appreciate any help.

assuming u have windows loaded on slave drive, the following could be attempted:-

1. in your [COLOR="Blue"]menu.lst [/COLOR]file of ubuntu 7.10 make entry for windows with correct partition no. (have a look at examples/ comments of menu.lst file for what entry is to be made; examples/ comments start with #)
2.  ubuntu disk should be set first in booting priority of hard disk.
3.  when u boot computer, GRUB will give u option for ubuntu and windows.

regards

---

### Post by marufaberlin on 2008-03-10
But normally you could just run ```
sudo update-grub
sudo grub-install /dev/hda
``` (replace /dev/hda with your hd)

---

### Post by sandysandy on 2008-03-10
> **marufaberlin said:**
> But normally you could just run ```
sudo update-grub
sudo grub-install /dev/hda
``` (replace /dev/hda with your hd)

grub is already installed. windows is required to be added to booting option of grub.

regards

---

### Post by marufaberlin on 2008-03-10
that doesn't install grub, it updates the menu.lst and then rewrites grub to the mbr,

---

