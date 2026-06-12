---
title: "Cannot remove grub!"
date: 2008-01-05
forum: General Help
---

### Post by Penguinw on 2008-01-05
can some one help?

I was doing a fresh install of my computer (Ubuntu + xp). so i completely formated my hd. i made a ext3, swap and a fat32 partition all completely blank. Everything went ok, when i put the xp disk in to reinstall xp it did the usual(the copying files onto the hard disk) but then when it rebooted to finish it came up saying grub error, i thought this was because grub may be installed on another hard disk, so i took all but the hard disk i was installing onto, out of my computer. Yet the grub error still came up, then i ran i a live Ubuntu cd (7.04 - thats what i'm on now) and did sudo apt-get remove grub, and it did something so i restarted but it still came up. So then i decided to totally remove all partitions on my computer and make it just unallocated space. Then I restarted (with no live cd in) but the grub error still came up! I have no idea where it is and why it is giving me the error. At the moment there is one single hard disk which is apparently completely blank, yet grub must be still installed somewhere..?
Before i deleted everything i knew i had 2 grubs were installed but i couldn't remove one of them.

Pictures:
[GParted]("http://i74.photobucket.com/albums/i276/penguinw/Screenshot.png")
[Boot Screen]("http://i74.photobucket.com/albums/i276/penguinw/Untitled.jpg")

I really need help please because i need to finish important work that uses windows programs
thanks.

---

### Post by yabbadabbadont on 2008-01-05
Grub is in the MBR, which is not affected when you delete all partitions.  I have had trouble with Win2k refusing to overrite the grub MBR in the past.  **[COLOR="Red"]If and only if[/COLOR]** you want to **[COLOR="Red"]completely wipe the drive[/COLOR]** so that XP will install it's own MBR, then you can use the dd command to write zeros to the first 512 bytes of the drive.  That will clear both the MBR and the partition table.  You'll have to be booted on a linux live cd to do this.
  
**[COLOR="Red"]Only do this if you want to clear the drive:[/COLOR]** ```
dd if=/dev/zero of=/dev/hda bs=512b count=1
```  This assumes that your drive is /dev/hda.  **Change the command for the correct device for your drive.**

---

### Post by Fir3chi3f on 2008-01-05
I would think that the fresh install of windows would overwrite the mbr. :confused:

But you could try this: [http://ubuntuforums.org/showthread.php?t=622828](http://ubuntuforums.org/showthread.php?t=622828)

---

