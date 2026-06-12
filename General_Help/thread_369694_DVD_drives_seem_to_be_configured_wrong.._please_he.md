---
title: "DVD drives seem to be configured wrong.. please help"
date: 2007-02-24
forum: General Help
---

### Post by billdotson on 2007-02-24
I have a Lite-On SATA DVD multi recorder and a LG Super Multi DVD burner (dvd+-rw and cd+-rw) and they seem to be acting funny with any type of program that depends on a DVD the program won't read them correctly or something.  They are also very slow to mount and unmount.

here is my /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=c51e7206-7183-4cee-b79f-142eb72cbc1b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb2
UUID=1e0d2ef5-41dc-4288-8518-4814ecc5c585 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0        /media/dvdrecorder   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1    /media/Windows_ntfs ntfs  nls=utf8,umask=0222 0    0
/dev/sdb4    /media/Backup_ntfs ntfs  nls=utf8,umask=0222 0    0
/dev/sdb7 /media/ext3 ext3 rw
/dev/sdb5   /media/FAT32   vfat   iocharset=utf8,umask=000   0   0
/dev/sdb6   /media/FAT32_2nd   vfat   iocharset=utf8,umask=000   0   0


Thanks you.  I am spending so much time just getting Ubuntu setup to where I can use it most of the time.  I have re-installed probably 8 times and I am still having annoying issues.

---

### Post by tgalati4 on 2007-02-24
Sounds like one of your drives are failing.  This can cause bus slowdowns.  It's common.  A google search on your drive model will give you a clue as to its reliability.

There is a check CD option on the live CD.  It reads the entire disk and creates an md5 checksum.  If the drive is bad or the media is poor, it will take forever to read the checksum.

Post back with your DVD model numbers and what you found on google.

Do the drives work OK in Windows?

---

### Post by billdotson on 2007-02-25
the drives seem to work fine in Windows.  They won't burn at the speed they advertised but as long as they burn they work.

[http://www.newegg.com/product/product.asp?item=N82E16827136103](http://www.newegg.com/product/product.asp?item=N82E16827136103) here is the LG burner that I got from newegg.com seems to have good reviews.

[http://www.newegg.com/product/product.asp?item=N82E16827106047](http://www.newegg.com/product/product.asp?item=N82E16827106047) here is my Lite-On SATA drive I got @ newegg.com.  It also looks like it has good reviews.

I usually look at reviews and common issues before I purchase these things and it seems that the things about these drives are that they might be a little loud and might not burn as fast as they say they do.  I saw in a review that some of the LG multi-burners have about a 10-15 second delay when reading discs.  

The weird thing is that I have installed vobcopy to copy the vob files off of my DVDs I have recorded my TV shows on and when I put a DVD in either drive all I have to do is type vobcopy and it finds the drive and rips it without any issues.  But in gnomebaker or acidrip or dvd::rip they all seem to have trouble finding the drives and/or working with them.  In gnomebaker if I try to blank a cd+-rw it just locks up with the LG burner and I have to reboot to get it out.  

It seems it has done the same thing in Windows using Roxio Easy Media Creator 7 a couple times.  But if I try to do it in the SATA DVD drive in gnomebaker it says it isn't a valid drive or something.  When I try to format a DVD it says it is completed after like 5 seconds but it didn't format or delete anything off of the disc.  In Windows I can format DVDs perfectly fine.

I don't know what is going on but it is annoying

---

### Post by tgalati4 on 2007-02-25
Try unplugging one of the drives and see if Ubuntu works any better.  Perhaps  having both SATA and IDE "media" drives is causing a kernel problem.

Sounds like you have it narrowed down and your hardware appears intact.  Have you tried searching the gnomebaker bug list, perhaps you are not the only experiencing problems with SATA DVD writers.

---

