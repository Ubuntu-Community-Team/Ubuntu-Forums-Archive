---
title: "How do I use aptitude to remove everything but the most basic packages?"
date: 2008-01-12
forum: General Help
---

### Post by rocketman768 on 2008-01-12
I want to use aptitude to remove all of the packages (including gnome and all that jazz) except the basic stuff and things required to have network connectivity and sound. Is there an easy way to do this?

---

### Post by ~LoKe on 2008-01-12
I'd like to know this as well.  The most I know of is that you can use Synaptic to list packages installed, but that doesn't include base (OpenOffice, Gnome, etc).

---

### Post by rocketman768 on 2008-01-12
The reason I ask is because I am stripping the ubuntu live cd down inside a chroot environment and then adding my own stuff since live-helper is indeed *not* so helpful.

---

### Post by p_quarles on 2008-01-12
The only way to do that would be to make a *loooong* list of the packages you wanted to nuke and then:
```
sudo aptitude remove *looooong-list-of-packages*
```
If you make such a list, you could also put it into a text file and use xargs to send the file to the aptitude command. 

That's really burdensome, though. The easiest way to do this is to operate in the other direction: start with the [Ubuntu minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD"), and install what you need.

---

### Post by kellemes on 2008-01-12
> **~LoKe said:**
> I'd like to know this as well.  The most I know of is that you can use Synaptic to list packages installed, but that doesn't include base (OpenOffice, Gnome, etc).

Not sure what you mean..
Isn't "dpkg -l" giving you the info you need?

---

### Post by Ink-Jet on 2008-01-12
I think it's seriously just removing each package one by one.

---

### Post by kellemes on 2008-01-12
> **p_quarles said:**
> The easiest way to do this is to operate in the other direction: start with the [Ubuntu minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD"), and install what you need.

Indeed..

---

### Post by rocketman768 on 2008-01-12
Crap. And I don't think the minimal ubuntu image is going to do me much good. It just basically has a kernel, initrd image, and isolinux. I think I need a live distro with a root filesystem sitting somewhere that i can chroot into and install packages.

---

### Post by p_quarles on 2008-01-12
> **rocketman768 said:**
> Crap. And I don't think the minimal ubuntu image is going to do me much good. It just basically has a kernel, initrd image, and isolinux. I think I need a live distro with a root filesystem sitting somewhere that i can chroot into and install packages.
Seems like this would be much simpler if you just installed Ubuntu minimal on a virtual machine. That way, you could build the installation that you want, and it would be relatively easy to replicate the package list from that installation.

---

