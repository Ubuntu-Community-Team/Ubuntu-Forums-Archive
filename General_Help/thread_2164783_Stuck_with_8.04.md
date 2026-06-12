---
title: "Stuck with 8.04"
date: 2013-08-01
forum: General Help
---

### Post by bill6 on 2013-08-01
So a while back I installed Ubuntu 8.04 (Hardy Heron), under the impression I would magically be able to use the terminal style of the distro. Well I'm an idiot, and I can't. Now I'm attempting to install 12.04 to keep it simple, be regardless of what I do (change the computers boot order, open the one-time boot order menu, etc) I can't boot from a CD to install the new distro, and it always boots in 8.04. My question is, is there a way I can delete the current partition on 8.04 with a command in order to re-install Ubuntu?

---

### Post by Bashing-om on 2013-08-01
bill6; Hi ! Welcome to the forum.

Lemme ask the obvious and get that out of the way -> you have set the bios boot 1st priority as the CD drive, no ?
Then the checksum of the downloaded .iso file was verified (md5sum), and:
Did you verify the disk burn integrity ( in the liveCD boot options screen).
version 12.04 was the last version of ubuntu that will fit onto a CD ...

With all the above, one is sure to boot to something !

[INDENT][INDENT]its a computer, there has to be a reason
[/INDENT][/INDENT]

---

### Post by TheFu on 2013-08-01
During boot-up - before any OS is attempted, you need to press the "magic function key" for your system to tell it to boot from the CDROM drive.  Different machines have a different funcgtion key for that purpose.  F7, F8, F10, F12, F1 ... I've seen them all used.  Or go into the BIOS and set the boot order to check the optical drive first.

After you boot of the CD, you can delete the partitions, but I don't think it is possible to delete partitions that are actively used.

If your computer is old, you might not have a PAE compatible CPU - that means you need to use the "Ubuntu Alternate Install CD" to boot and install a non-PAE kernel.  I'd look up the exact CPU you have and verify that it supports PAE if it is more than a few yrs old.

---

