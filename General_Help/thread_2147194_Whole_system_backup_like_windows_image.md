---
title: "Whole system backup like windows image?"
date: 2013-05-21
forum: General Help
---

### Post by Tjkhan on 2013-05-21
I was thinking, Is any way to create whole system backup like windows image? Example my OS crashed, is there any way to make a backup? with all installed programs so that I can restore the whole system?
Nothing important, just asking

---

### Post by prodigy_ on 2013-05-21
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://wiki.archlinux.org/index.php/Full_System_Backup_with_rsync](https://wiki.archlinux.org/index.php/Full_System_Backup_with_rsync)
[http://www.aboutdebian.com/tar-backup.htm](http://www.aboutdebian.com/tar-backup.htm)

---

### Post by HermanAB on 2013-05-21
You can use clonezilla.

---

### Post by p-dh on 2013-05-21
One of the easiest to use is the CLI program dd. The basic use is:
> dd if=<input file or drive> of=<output file or drive>
For instance, if I wanted to make an image of my operating system, which is on the first partition of the first drive, directed to a file on another drive (which is the second partion of the first drive), I would type:
> dd if=/dev/sda1 of=/dev/sda2/os.iso
This will create an image file that I can mount if I want to - to copy files from it, for instance. Or I can reverse the command and return that image to the original partition. The second partition has to have enough space for the image file.

Peace,
Paul :cool:

---

### Post by ibjsb4 on 2013-05-21
> **HermanAB said:**
> You can use clonezilla.

Works great

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by Mark Phelps on 2013-05-21
+1 for Clonezilla.  Use it all the time to do image backups.  Little tricky to use, as unlike other imaging solutions, you have to enter the DESTINATION first, not the SOURCE. If you check their website, they also have instructions for copying the ISO to your install so you can boot using the ISO, negating you having to boot from CD or USB to do a backup.

---

