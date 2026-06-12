---
title: "Partition resize - help please!"
date: 2007-05-19
forum: General Help
---

### Post by scradock on 2007-05-19
I've made the leap - switched from Windows XP to Edgy and then to Feisty, on my HP laptop (Pavilion zv6000). Now after setting up several Linux partitions in 30 GB of my 95 GB hard-drive I want to reduce the WXP primary partition from 65 GB to 35, and free up lots of lovely space for Ubuntu. I've cleaned stuff out and got the WXP contents down to 16 GB, so it should be fine.

BUT Gparted won't resize the NTFS partition - says it's corrupt. Partition Magic in WXP says the same - error 1529 - Information mismatch in directory entry. The PM manual says this means one of the WXP system files has an incorrect attribute set, inconsistent with its internal value. Running CHKDSK /F repeatedly in WXP start-up eventually gives me a report that there are no errors, but Partition Magic still refuses to resize the WXP partition (tries to do it while WXP is rebooting, fails with the same error.

I'm using ntfs-3g in Feisty; now the WXP volume is reported as corrupted when I try to mount it in Feisty, and I can only mount using the "force" option in fstab.

I've tried doing all this without using ntfs-3g; without any fstab entry for /dev/hda1. As soon as I open Gparted the WXP drive mounts as /media/XPBoot, even if I don't have a /media/XPBoot directory set up. Where does that come from?

Anyone out there able to help me? It's only an attempt to salvage 30 GB of my drive, but it's getting annoying. Ubuntu (both Feisty and Edgy) are working fine, and I don't have any reason to suppose re-installing them would help.

I don't have any problems booting; just can't resize my WXP partition. I'm still resisting the temptation to wipe it completely............

scradock

---

### Post by Sef on 2007-05-19
Check out [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") or [Trinity Rescue Kit]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12").

---

### Post by scradock on 2007-05-19
Thanks, Sef. I'll burn a CD of one of those, in case I can't boot at some stage.

At the moment I can boot just fine - grub knows what to do, and WXP boots OK.

I just can't resize my WXP partition with the available tools.......

Anyone have any idea what I can do? Please?????

scradock

---

### Post by scradock on 2007-05-22
Well, since no-one seems to be coming up with any answers, here they are:-

ntfsresize - already installed in Feisty. 

Does the first half of the trick - shrinks the ntfs file-system. 

Then fdisk to dlete and recreate the partition itself.

Instructions? Google "ntfsresize"

Hope that helps someone.......

---

### Post by merlinus on 2007-05-22
I have found the Gparted live cd to work very well for these kinds of tasks.

Burn the .iso as a disk image, and boot from it.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by ukripper on 2007-05-26
> **scradock said:**
> I've made the leap - switched from Windows XP to Edgy and then to Feisty, on my HP laptop (Pavilion zv6000). Now after setting up several Linux partitions in 30 GB of my 95 GB hard-drive I want to reduce the WXP primary partition from 65 GB to 35, and free up lots of lovely space for Ubuntu. I've cleaned stuff out and got the WXP contents down to 16 GB, so it should be fine.

BUT Gparted won't resize the NTFS partition - says it's corrupt. Partition Magic in WXP says the same - error 1529 - Information mismatch in directory entry. The PM manual says this means one of the WXP system files has an incorrect attribute set, inconsistent with its internal value. Running CHKDSK /F repeatedly in WXP start-up eventually gives me a report that there are no errors, but Partition Magic still refuses to resize the WXP partition (tries to do it while WXP is rebooting, fails with the same error.

I'm using ntfs-3g in Feisty; now the WXP volume is reported as corrupted when I try to mount it in Feisty, and I can only mount using the "force" option in fstab.

I've tried doing all this without using ntfs-3g; without any fstab entry for /dev/hda1. As soon as I open Gparted the WXP drive mounts as /media/XPBoot, even if I don't have a /media/XPBoot directory set up. Where does that come from?

Anyone out there able to help me? It's only an attempt to salvage 30 GB of my drive, but it's getting annoying. Ubuntu (both Feisty and Edgy) are working fine, and I don't have any reason to suppose re-installing them would help.

I don't have any problems booting; just can't resize my WXP partition. I'm still resisting the temptation to wipe it completely............

scradock

Try Partition Magic 8, the easiest way.

---

### Post by rillip on 2007-05-26
Uh, guys, he already tried using gparted and partition magic.... he said so above.

To scradock, I'm sorry no one came up with your answers, but glad you shared the for the next person who looks!

---

### Post by AndrewGene on 2007-05-26
^^^you've already helped someone

---

### Post by merlinus on 2007-05-26
> **scradock said:**
> Well, since no-one seems to be coming up with any answers, here they are:-

ntfsresize - already installed in Feisty. 

Does the first half of the trick - shrinks the ntfs file-system. 

Then fdisk to dlete and recreate the partition itself.

Instructions? Google "ntfsresize"

Hope that helps someone.......

OK, and thanks.  I downloaded ntfsprogs using Synaptic, but where can I find it in Feisty?

-merlin

---

