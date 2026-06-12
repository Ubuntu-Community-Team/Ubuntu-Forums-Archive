---
title: "Is it possible to move root during an upgrade?"
date: 2014-04-16
forum: General Help
---

### Post by m-dw on 2014-04-16
My current root drive is very old (4 years uptime, 1 bad sector, SMART reports it running at about 80 Celcius).  I've successfully moved everything except root and swap off it onto a SATA disk that also supports /home.  There is a spare 30Gig physical partition (which currently has /usr/share on it) that I can delete and reuse (swap + /)

Can I do this as part of the 14.04 upgrade, or would I be better off installing from scratch?

Also this physical partition starts at sector 419442688 (after the 200Gig /home).  Is that a problem?  I remember that when I started out you needed to put /boot near the beginning of the disk, but not sure if that's an issue any more.

---

### Post by Impavidus on 2014-04-16
I don't think you can move the root partitions during an upgrade. You could do it before or immediately after, but I would just do a fresh install.

A root (or /boot) partition too far from the beginning of the disk can be a problem, but I think this should be fine on most modern systems.

---

### Post by monkeybrain20122 on 2014-04-16
I am not sure what you are trying to achieve here, sounds like you want to move the existing / to your external drive and then upgrade. Is that it?
This is not too difficult (some complications may arise because not sure where your /home was before and if its uuid has been changed)

However, a fresh install is always (a lot) faster and safer than 'upgrade', which leaves many systems broken based on reports on these forums, and there can also be undiscovered problems that only manifest themselves later. "upgrade" is too complex and fragile a process to rely on IMO.

If I were you I would simply do a clean install on the free space on your external drive,--may want to shrink it a bit, root partitions typically don't need 30Gs,-- designate it as / and use the same /home without formatting it. Since you already have a separate /home that makes fresh install even easier and even less reason for 'upgrade'.

---

### Post by coldcritter64 on 2014-04-16
> **m-dw said:**
> My current root drive is very old (4 years uptime, 1 bad sector, SMART reports it running at about 80 Celcius).  I've successfully moved everything except root and swap off it onto a SATA disk that also supports /home.  There is a spare 30Gig physical partition (which currently has /usr/share on it) that I can delete and reuse (swap + /)

Can I do this as part of the 14.04 upgrade, or would I be better off installing from scratch?

Also this physical partition starts at sector 419442688 (after the 200Gig /home).  Is that a problem?  I remember that when I started out you needed to put /boot near the beginning of the disk, but not sure if that's an issue any more.

I have moved root partitions, by cloning to other partitions or drives and got them working/bootable. Do you know how to chroot into a broken install from a live cd/dvd/usb etc ? This is to fix any boot problems, that sometimes do crop up when moving systems about.

Installing from scratch sounds far easier, I'd say "YES". :) 4 years; must put your install release at about "Lucid". I suspect, if that is so, you would need to possibly upgrade in a couple of steps, a fresh install is much easier, IF that is the case.

I've never use a separate /boot partition, so don't know about its placement. However I've installed Linux/Ubuntu installs all over the shop, including external drives and completely installed to within an extended partition at the extreme end of a 1 TB drive, about the last 30GB or so at the end of the 1TB drive was used. The boot folder and the kernels etc all were at the end of the drive and the system was perfectly usable.

Am I right in assuming you want to move root because of possible hardware issues, bad sectors etc ? May be an idea to do a "new" 14.04 install to the freshly formatted drive and keep the old system until all data and application configs etc you need are moved across. Basically, dual boot 2 Linux installs temporarily until you have 14.04 fully set up.

---

### Post by m-dw on 2014-04-16
Thanks both for replies.  It's not an external drive, it's an internal SATA drive which was previously dedicated to data storage (/home and /music) when the PC used to double as a media server.  I've now moved most of my data to a NAS, and /home is really only for my config files and for recording audio.

Existing /root is on a Hitachi Deskstar IDE drive (I think probably over 10 years old as I would have moved it from my previous system when I built this one).  I'll give the fresh install a go and see if I can ditch it for good.

Realistically I could move /home to a logical partition at the end of the drive and the plan the partitioning scheme a little better, but I'll try the easy way first.

---

### Post by m-dw on 2014-04-16
> **coldcritter64 said:**
> Installing from scratch sounds far easier, I'd say "YES". :) 4 years; must put your install release at about "Lucid". I suspect, if that is so, you would need to possibly upgrade in a couple of steps, a fresh install is much easier, IF that is the case.

It's not quite that old.  I originally ran SuSE 9.0 on this system, and switched to Ubuntu at 12.04.  It's now running 13.10 (upgraded three times).  The disk uptime is 4 years, it's real age is considerably more.  Am encouraged by your experience of installing at the end of the drive.

> **coldcritter64 said:**
> Am I right in assuming you want to move root because of possible hardware issues, bad sectors etc ? May be an idea to do a "new" 14.04 install to the freshly formatted drive and keep the old system until all data and application configs etc you need are moved across.

Yes, that's correct.  SMARTMON is now reporting a drive temperature of 97 Celsius.  I had thought that there was an unrecoverable sector, but that's not being reported now, and the drive isn't even warm to the touch, so who knows?  May last another 4 years.

---

### Post by monkeybrain20122 on 2014-04-16
> **m-dw said:**
> 
Realistically I could move /home to a logical partition at the end of the drive and the plan the partitioning scheme a little better, but I'll try the easy way first.

You can do that after you reinstall your system. With fsarchiver is really straight forward to clone your /home, then delete it and repartition the drive to your liking (don't touch the root partition) and then restore the clone to a different partition.

---

### Post by m-dw on 2014-04-16
Or... I could do that before I re-install, so I can install into a physical partition at the beginning of the drive when I do the fresh install, followed by a /home to fill the rest of the disk.  If I reinstall into the free space in the middle of the drive and it works, I'm more likely to leave it as it is.

---

