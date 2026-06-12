---
title: "Is Xubuntu suitable for Compaq Armada?"
date: 2012-12-29
forum: General Help
---

### Post by paul1945 on 2012-12-29
I have an old Compaq Armada M700 notebook that I am retiring from active service; it is being replaced by a later desktop that runs the latest version of Ubuntu. I would like to junk the cluttered and very slow Windows 200 distro on the notebook and replace it with a Linux one, so I can use it as my "odd jobs" machine in tandem with my Ubuntu machine, for word processing and other tasks. 
So I am wondering whether it has enough grunt for Xubuntu, or if I should look to another distro.
Specs are:
Processor: Pentium 3 - 600 Mhz.
Memory: 384 mb.
Hard drive: 40 GB
Display: 1024 X 768
Thanks in advance.

---

### Post by sudodus on 2012-12-29
> **paul1945 said:**
> I have an old Compaq Armada M700 notebook that I am retiring from active service; it is being replaced by a later desktop that runs the latest version of Ubuntu. I would like to junk the cluttered and very slow Windows 200 distro on the notebook and replace it with a Linux one, so I can use it as my "odd jobs" machine in tandem with my Ubuntu machine, for word processing and other tasks. 
So I am wondering whether it has enough grunt for Xubuntu, or if I should look to another distro.
Specs are:
Processor: Pentium 3 - 600 Mhz.
Memory: 384 mb.
Hard drive: 40 GB
Display: 1024 X 768
Thanks in advance.

I suggest that you install Lubuntu 12.04 from ***the alternate CD***

[[COLOR="RoyalBlue"]http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/[/COLOR]]("http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/")

The alternate CD is better for installation when there is so small RAM. Lubuntu is even lighter than Xubuntu, and works better with old hardware.

You can install xubuntu-desktop into Lubuntu if you want to (after it is installed and rebooted).

```
sudo apt-get install xubuntu-desktop
``` This will give you the extra tools of Xubuntu and also the option to select Xubuntu, Lubuntu or even plain Openbox at the login screen.

*Edit*: An alternative is to try some extremely small distro, if even Lubuntu will be slow. We can come back to that later.

---

