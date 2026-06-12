---
title: "Ubuntu filesize Limit"
date: 2007-04-18
forum: General Help
---

### Post by killerdragon on 2007-04-18
Does anyone know off hand what the largest filesize ubuntu's file system will handle?
I know FAT32 has a limit of 4gig, I was wondering if ubuntu has the same limitation.

---

### Post by viciouslime on 2007-04-18
I believe the maximum file size on an ext3 partition is 2TB. The 4GB limit certainly doesn't apply. If you use reiserFS I think you can have 8TB files.

---

### Post by dschmitt on 2007-04-18
Ubuntu itself does not have file size limits --- It depends what file system you are using the standard is ext3.

Filesystem 	File Size Limit 	Filesystem Size Limit
ext2/ext3 with 1 KiB blocksize 	16448 MiB (~ 16 GiB) 	2048 GiB (= 2 TiB)
ext2/3 with 2 KiB blocksize 	256 GiB 	8192 GiB (= 8 TiB)
ext2/3 with 4 KiB blocksize 	2048 GiB (= 2 TiB) 	8192 GiB (= 8 TiB)
ext2/3 with 8 KiB blocksize (Systems with 8 KiB pages like Alpha only) 	65568 GiB (~ 64 TiB) 	32768 GiB (= 32 TiB)
ReiserFS 3.5 	2 GiB 	16384 GiB (= 16 TiB)
ReiserFS 3.6 (as in Linux 2.4) 	1 EiB 	16384 GiB (= 16 TiB)
XFS 	8 EiB 	8 EiB
JFS with 512 Bytes blocksize 	8 EiB 	512 TiB
JFS with 4KiB blocksize 	8 EiB 	4 PiB
NFSv2 (client side) 	2 GiB 	8 EiB
NFSv3 (client side) 	8 EiB 	8 EiB
(accquired from: [http://www.suse.de/~aj/linux_lfs.html](http://www.suse.de/~aj/linux_lfs.html))

---

### Post by akshaysrinivasan on 2007-04-18
The file size limits depend on the filesystem ,as pointed above .Wikipedia has details of all the filesystem and file size limits.

---

### Post by Oki on 2007-04-18
Here you will find a good overview over the different file systems and what they can handle. 
[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

---

