---
title: "iPod and USB Automount in Gutsy"
date: 2007-12-11
forum: General Help
---

### Post by KevLeviathan on 2007-12-11
Hi guys,
I'm running Gutsy on my laptop and I'm having some issues with USB.
My USB key only auto-mounted the first few times. Since then, it will not automount unless I reboot the computer and leave it plugged in while the computer boots.
Second, my iPod will not automount either HOWEVER one out of every 10 times i type lspci in a terminal, it will autodetect the ipod anautomount it.
Any ideas?

NINJA EDIT:
By following the suggestions here
[https://bugs.launchpad.net/ubuntu/+bug/130367](https://bugs.launchpad.net/ubuntu/+bug/130367)
I seem to have fixed it..



Fixing the problem:

Editing fstab and removing these lines:

#/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
#/dev/sdb1 /media/sdb1 vfat defaults 0 0
#/dev/sdc1 /media/sdc1 vfat defaults 0 0

Now Pendrives and cdroms works fine again!

EDIT 2 (not so ninja)
Well I've rebooted and now nothing works again.. so.. :-\

---

