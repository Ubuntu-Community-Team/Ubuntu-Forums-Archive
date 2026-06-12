---
title: "Virtualization/Emulation Stuff"
date: 2007-02-19
forum: General Help
---

### Post by Raptor45 on 2007-02-19
I've always wanted to get windows running inside linux, but never had time to look into how to do it. I believe I'd want to use QEMU or VMWare?

I found this howto:
[https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)

However, I already have windows XP Installed on my system, and that involves installing the OS fresh. Is there any way I could just "run" the OS as it is installed? Is that not the preferred way of doing things in this case?

This is not a subject I have really looked into, so any additional general info would be great.

---

### Post by xopher on 2007-02-19
You should also have a look at Virtualbox, a nice, more graphical fully GPL'd virtualization program. [http://www.virtualbox.org/](http://www.virtualbox.org/)

And to the other question, I really don't know. It might work though. If you set the program up to boot from where you currently have windows xp installed..

---

### Post by Raptor45 on 2007-02-19
That doesn't appear to work with 64 bit, so no-go unfortunately.

Figured I'd just install win2k with qemu for starters. Unfortunately, its the upgrade version and it won't detect when I switch to a win95 disk. Any idea how I can get the setup to "see" the disk change?

---

### Post by bob-aptllc on 2007-02-23
If you choose to install VirtualBox on Edgy, here is a good tutorial that helped me. Look at it before trying to install VirtualBox so you don't break your Synaptic and have to reinstall Edgy like I had to. [http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html](http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html).

---

