---
title: "GRUB bootdisk?"
date: 2007-04-01
forum: General Help
---

### Post by marco999 on 2007-04-01
hello I was wondering if I could obtain a grub boot disk for Ubuntu?

The situation:

I want to install ubuntu on a ejectable hard drive enclosure. This is placed inside my computer. To swap the hard drives I need to turn off the computer, unlock the drive, and then insert the new one. This I do regularly.

The problem:

Whenever I swap a hard drive with ubuntu on it, for say a storage drive; and then swap the ubuntu drive back in - I experience the GRUB error 22 message. This indicates that the hard drive cant be found; even tho it is reinserted.

The possible solution:

I thought that if I could boot into ubuntu off of a bootdisk(like the ones in the old day of redhat 3.2) then I could boot into ubuntu no problems. Does anyone have such a bootdisk, or is willing to make one? I was thinking that it could have a modified version of GRUB on a cd/floppy and it could read the menu.list from the /boot/GRUB/ directory and use the options from it. That way when the file is updated for a new kernel the options will change to go along with it.


Could someone program this? The idea would be to make it totally universal with any version of Linux and/or GRUB; these together would allow the user to boot from any OS on their system/server.


Or if possible is there a way to boot into Linux via a bootdisk and bypass grub all together? Or if there is a bootdisk that will do this already please tell me about it.


Thanks; hopefully I can solve my problem.

Marco999

---

