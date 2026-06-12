---
title: "i messed up my root partition real bad, even though i didn't really need to..."
date: 2023-07-26
forum: General Help
---

### Post by superpou1 on 2023-07-26
So, recently i was moving my pc to a new case, and i connected my 4 drives with different sata cables than they were connected before. One of the sata cables was loose and often disconnected if i just barely touched it. That cable was always connected to the drive i had ubuntu on, and when it disconnected i still was able to boot to grub, which i never questioned. Turns out, that grub was installed to a different drive. idk, it just always happens with the ubuntu installer if i don't force to install to a different partition. so, after i re connected my drives in the new case, i connected the cables to different drives, and i wasn't able to boot to ubuntu at all. i thought something is wrong with my drive, so i booted up a live usb to check what's wrong, where i saw that my drive didn't have an efi partition at all, just the root partition of ubuntu. keep in mind, i didn't know that the efi partition was actually on a different drive that was unluckily connected to that faulty sata cable. so, in gparted, i noticed there was some "microsoft reserved partition", i deleted that and then i tried to shrink my root partition to make space for an efi partition without thinking it through and without even a backup like a dumbass, and i accidentally chose to also move the partition to the left where that microsoft partition was (exactly 16mb) and then i noticed it's going to take a REALLY long time, so i cancelled it thinking i can revert it or something... i was so wrong. i tried using testdisk, and that detected the part of the partition that had moved, and i could view files on that, which was not so essential stuff, such as programs in the /bin folder. it also detected the unmoved parts of the partition, but it couldn't read the files on them most likely because it was missing essential partition data. though, i think most of the data is still mostly intact, because i was able to read virtual disk images i downloaded i created at some point, so that means the rest of my data is most likely still there. so what i am thinking is, could i possibly somehow glue that partition back together, OR, i could recover most of the data and put it into a new ubuntu installation? if so, what should be the procedure?
(btw i made a backup of the drive as an img on another drive just in case something really bad happens and my data actually gets completely erased)

---

### Post by oldfred on 2023-07-26
Any interruption of a move totally corrupts data. As you have seen part of data is moved & part is not.
And since overlap it gets very difficult on what gparted was doing. 
You can try photorec, if deeper search in testdisk has not worked. But it takes hours/days if multiTB drive and only recovers files by extension/type. You do not need to recover system. Was /home or most of data also on same drive?
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec) & 
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

Standard rule is if repair takes more than an hour, better to reinstall & restore from backups. But requires good backups in advance.

I like to have an ESP on every larger drive & small install with only some repair tools added, but not all my apps. Just for emergency boot.
But my older Asus would get confused with too many UEFI entries, so did not always work well. 

UEFI/BIOS sets drive order by SATA port order. But now NVMe drives seem to be first drive, but when listing drives they are last?

I converted to using SATA cables with the locking clip. My old parallel cables often came unplugged when in case as they were bulky and had no lock. So after first issue with one SATA cable converted to locking cables, since they are available.

---

### Post by superpou1 on 2023-07-26
well, i don't have too important data, i store important data that i don't use so often or is too big on a big hdd, but i definetly had a lot of stuff on my root ubuntu partition too, but i think the file structure was pretty important for me too for some games/programs such as minecraft, but i don't think photorec can recover the file structure of such things, so that will be pretty useless now

---

