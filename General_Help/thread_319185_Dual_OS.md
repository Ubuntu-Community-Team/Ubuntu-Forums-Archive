---
title: "Dual OS"
date: 2006-12-15
forum: General Help
---

### Post by Soulstorm on 2006-12-15
Preface: I'm not exactly sure what forum to post this for the most reliable help, so I have placed it in the general forum.

I have Ubuntu and Windows on the same desktop machine.  I use lilo boot during startup to choose which OS I want to go into.  (Don't ask me why I still boot into Windows and use it). As you know, Ubuntu can read Window's files, but Windows cannot see the Ubuntu partition.  My question is: Is there a way I can boot both OS's at the same time and be able to switch between them back and forth?  If so, how would I go about doing this configuration.

---

### Post by PurplePenguin on 2006-12-15
Yes, there is a way (sort of).  You can install a virtual machine.  Just install one of the different products in the [VMWare]("http://en.wikipedia.org/wiki/VMware#VMware_Player") family (VMWare Player, VMWare Server, etc).  This will let you boot into Windows, then open up a window that's running whichever kind of linux you decide to install.

Or you can do it the other way, where you boot into linux, but open up a windows virtual machine session.

This isn't exactly the same as booting into the OS after a reboot, though.  I don't think that 3D acceleration works in the virtual sessions - I've only played with VMWare a bit, though (actually, I installed an Ubuntu virtual machine before switching to it from OpenSuse!).

---

### Post by Soulstorm on 2006-12-15
Oh, I forgot about the virtual windows in Ubuntu... Although does this allow for both OS's to read, copy, move, and delete from the other OS's?

---

### Post by PurplePenguin on 2006-12-15
I've never tried it personally, but I do believe that copy and paste to/from the host machine works.

I'm sure that there are a ton of guys here who use VMWare Player/Server, so hopefully they can let you know a bit more about it. :)

---

