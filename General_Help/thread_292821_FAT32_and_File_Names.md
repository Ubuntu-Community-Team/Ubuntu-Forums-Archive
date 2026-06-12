---
title: "FAT32 and File Names"
date: 2006-11-04
forum: General Help
---

### Post by Roger Mudd on 2006-11-04
I'm in the process of attempting to upgrade from Dapper to Edgy and I wanted to back up all the music I ripped to Ogg last weekend.
I have three drives on my computer. An internal SATA drive for XP (NTFS), an internal IDE drive (EXT3) for Ubuntu and an external USB drive (NTFS) that I was using to back up information from my XP install. The music is stored in my /home directory on the linux install.
As I can't write reliably to NTFS from Ubuntu, I used the Dapper Live CD and Gparted to shrink the external drive's NTFS partition and create a 25GB FAT32  partition on which I can place shared data accessible to both operating systems. All good so far.
I then issued the following command in an effort to recursively back up the home directories of all users on my Ubuntu install (including the music I ripped last weekend):
```
sudo cp -r /home /media/usbdisk/home
```
This seemed to work, however, a good number of the files could not be copied. Apparently there were some symbolik links for some of the Gnome file and other file names included characters like semi-colons, parenthesis, apostrophe's, etc. The cp command seemed to choke on these files.
Does FAT32 not recognize those charactersin file names? Is there any way  around this symbolic link issue?

---

### Post by kidders on 2006-11-04
No :-( FAT32 is *hugely* restrictive in terms of what you can call things. It also doesn't support the notion of a symbolic link, among many other things. You'll have to remove all such incompatibilities before transferring files from a "normal" filesystem onto a FAT one.

One possible alternative would be to wrap all your music up in a tarball, and copy *that* onto your FAT partition.

**Edit:** Be careful with "sudo cp". That will rewrite the ownership of all the destination files ... not that it matters with FAT32 anyhow ... but in general, you might find "sudo cp -dpR" preferable to "sudo cp -R".

---

