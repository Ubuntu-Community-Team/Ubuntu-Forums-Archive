---
title: "moving filesystem to a different partition"
date: 2008-06-15
forum: General Help
---

### Post by name_name on 2008-06-15
I have ubuntu set up on a 160 GB sata drive there partitions are basically 5 GB ubuntu (ext3), 5 GB free space (vfat), 150 gb free space (vfat), and a small swap partition. 

I set it up like this thinking I could use 5 gb for ubuntu, 5 for windows XP and 150 for storage, but that was a mistake. The 5gb for ubuntu is too small for updates, so is there any way I can combined it with the 5gb vfat partition I have. So then I have 10gb ext3 and 150gb vfat? Would I need to to do a complete reinstall? If so what files/dirs would I need to backup /home/ of course, but anything else.... please help.

---

### Post by Het Irv on 2008-06-15
You can boot to a Live CD and use Gparted to redo your partitions, but I have two warnings:
One - backup, backup, backup.  Just in case it doesn't work
Two - It might take a while.   Hours, depending on how exatly you change them around, it could take from 2 hours to 6, or maybe even longer.

---

### Post by name_name on 2008-06-15
> **Het Irv said:**
> 
One - backup, backup, backup.  Just in case it doesn't work


What should I back up? So there no simple way to merge those two paritions other then deleting them and making a new install.... :-(  I know it only takes 5 minutes to reinstall but I don't want to have to reconfigure and reinstall everything (GL Desktop, Wine, VLC, XMMS, Totem codecs, etc, etc.)

> Two - It might take a while. Hours, depending on how exatly you change them around, it could take from 2 hours to 6, or maybe even longer.

I've partitioned and formated drives before and they never take *that* long. Are you talking about memtest, that can take a while. :???:

---

### Post by Het Irv on 2008-06-15
I don't know how or even if you can combine partitions, but you can resize partitions (that is what might take a while).  If it is possible you can shrink your storge partition.  That way if you ever need Windows it is there.  Sad to say but it's not a bad idea to have Windows as a fallback.  About once a month I find something I need it for.

---

