---
title: "Accidently deleted partition - anyway to get it back?"
date: 2007-01-16
forum: General Help
---

### Post by idn on 2007-01-16
I recently installed windows, and during the install i accidently deleted a ext3 partition - it didnt format it, just deleted the partition, so now it is just unallocated space.

Is there anyway I can recreate the partition and get back all the files on it? Like I said I didnt format it, because windows came up with some error saying it couldnt created the new partition, but it managed to delete the old one anyway, i dunno.

Like I said, in gparted, the sapce is now just listed as 'unallocated space'

Thanks!

---

### Post by az on 2007-01-16
You can boot the live cd, and run parted from the command line.  It has a rescue mode which will search a part of the disk (or the whole thing) and if it detects a useable filesystem there, it will offer to add the partition to the partition table.


sudo parted /dev/hda

rescue

and then key in the approximate area where that partition used to be.

---

### Post by Sef on 2007-01-16
Check out [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").

---

### Post by wersdaluv on 2007-01-16
I have installed testdisk using Adept Package Manager but I don't know how to run it. I tried running it using Alt+F2 but it won't work. What should I do?

---

### Post by idn on 2007-01-16
> **azz said:**
> You can boot the live cd, and run parted from the command line.  It has a rescue mode which will search a part of the disk (or the whole thing) and if it detects a useable filesystem there, it will offer to add the partition to the partition table.


sudo parted /dev/hda

rescue

and then key in the approximate area where that partition used to be.

Ok, the partition is on, or was sdb4, it only had multimedia files on it - no system files, so i should be able to run it from my linux install, ill give it a go...

---

