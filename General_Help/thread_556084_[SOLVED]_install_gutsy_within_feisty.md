---
title: "[SOLVED] install gutsy within feisty?"
date: 2007-09-20
forum: General Help
---

### Post by jabster on 2007-09-20
Hi.

Could someone tell me how, if it's even possible, to install gutsy inside a VM on my feisty box?

I've looking at VMware, which didn't install from the ubuntu repositories, and xen, but I have yet to figure out if either one will do what I want. I want to install gutsy and try it out (especially kde4) without wiping my HD and running a beta.

The latest suse live CDs don't work. The latest nightly doesn't even start X, and beta2 barely works (every app opens, but crashes as soon as I click; kicker doesn't start at all, etc).

Any help appreciated.

thanks,
john

---

### Post by angryfirelord on 2007-09-20
I use VirtualBox which works like a dream. I tried the Gutsy cd in there without issues. I also found it easier to use than VMWare.

[http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads")

You can add it to your sources.list (don't forget to install the key) so you can use it with apt-get.

---

### Post by monoufo on 2007-09-20
dude, this is what partitions are for.  You could have 23 kinds of linux and 4 kinds of windows if you really wanted, provided your hard drive was large enough.

---

### Post by angryfirelord on 2007-09-20
> **monoufo said:**
> dude, this is what partitions are for.  You could have 23 kinds of linux and 4 kinds of windows if you really wanted, provided your hard drive was large enough.
True, but that's not always practical, especially if you're going to just wipe it off the drive as soon as you're done playing with it. Plus, VirtualBox is fun! :D

---

### Post by g2g591 on 2007-09-20
download an install cd (daily build so you don't have to install so many updates) burn it, then install vmware server (or other vm utility like virtualbox) open vmware, create a machine, then when it prompts you to insert the disk, insert it.

---

### Post by wirelessmonkey on 2007-09-20
I run Gutsy in a VMware Server virtual machine from Feisty.... so yes.

---

### Post by rsambuca on 2007-09-20
> **angryfirelord said:**
> I use VirtualBox which works like a dream. I tried the Gutsy cd in there without issues. I also found it easier to use than VMWare.

Do you find that systems in the virtual environment work as well as if they were installed on your hard-drive?  I have found that you just never get a true feel for the distro in the virtual system.  It could be that my PC just isn't good enough to handle it, though.

---

### Post by jabster on 2007-09-20
angryfirelord: VIrtualbox == Hella-cool. Way easier than VMware.

monoufo: I realize that, but I have a little problem....it's called The Wife(tm). I need the stable, configured system running all the time. I can deal with occasional liveCD, as all I have to do is reboot and all is good again. So, while I understand partitioning, and have in fact done that in the past, it is too much of a PITA. Both from a usability standpoint, and from a marriage standpoint. :)

So I'm installing gutsy right now, from within feisty.

Hella-cool. (Needed to be said twice.)

thanks,
john

p.s.: rsambuca: I don't think you can ever get it working as if it were a real install, unless you have a massive SMP, MEGA-RAM machine. At least as far as desktops are concerned. I'm sure server uses are just fine, or "virtualization" wouldn't be such a huge buzz word right now. But I may be wrong.

---

### Post by angryfirelord on 2007-09-21
> **rsambuca said:**
> Do you find that systems in the virtual environment work as well as if they were installed on your hard-drive?  I have found that you just never get a true feel for the distro in the virtual system.  It could be that my PC just isn't good enough to handle it, though.
Well, it's going to be a bit slower because you're running an OS on top of an OS and there's no 3D support for virtual machines. But it gives you a general idea of what the OS is like and once you install it, it'll be faster (obviously). Who knows, maybe the future of Live CDs will have VM runtime libraries so you can try it without having to reboot your computer?

However, you do need some beefier hardware in order to run VMs. I got a Sempy 3400+ with 1GB RAM that does fine.

---

