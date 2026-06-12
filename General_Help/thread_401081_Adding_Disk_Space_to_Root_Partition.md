---
title: "Adding Disk Space to Root Partition?"
date: 2007-04-04
forum: General Help
---

### Post by sbjaved on 2007-04-04
I'm outta space in my root partition (which also houses /home)... How do i add free space from my windows partition to root partition? My windows partition has plenty of free space...

---

### Post by mertle on 2007-04-04
I used Gparted not too long ago to do just that. You have to unmount the drives being resized, which ya can't do while booted in Ubuntu, so I downloaded the .iso version ([http://gparted.sourceforge.net/livecd.php)](http://gparted.sourceforge.net/livecd.php)), burned it to a CD, booted to to it, and ran it that way. I'd read up on some tutorials/guides/manuals on the program before I tried it as resizing partitions can be a risky process. Make /sure/ you've backed everything up, just in case something goes wrong or you make a mistake.

Good luck.

- mertle

---

