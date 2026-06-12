---
title: "Perfect Backup"
date: 2007-07-05
forum: General Help
---

### Post by Cool Surfer on 2007-07-05
Ok, I finally managed to have a perfect setup of ubuntu. Everything seems to be working fine.
I want to take a backup of the os and burn it on a cd or dvd. Something like a ghost image.
How and what all do i need to backup pl.

Which software can do this.

Thanks

---

### Post by Cool Surfer on 2007-07-06
Any help pl:popcorn:

---

### Post by swisscow on 2007-07-06
Hi

I downloaded and burnt the RescueCd: [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

Then boot with that and run partimage. You can then make a perfect copy of each of your partitions which you can save where you want (e.g. burn to dvd). Some instructions here [HTML]http://www.psychocats.net/ubuntu/partimage[/HTML] - they start about halfway down.

Works a treat for me - have used it many times to restore back after I've tried out another OS. Only thing I have had to do after I restored is to reset the swap file UUID - instructions for this are in this thread: [HTML]http://ubuntuforums.org/showthread.php?t=414113[/HTML]

---

### Post by Cool Surfer on 2007-07-06
So hiren boot cd also has that feature to take backups-dump backups?
I have 20gb /
40gb /home
3gb swap partitios.

So I need to take backups of just home? Any way to make it fit on a 4.7gb dvd?

Thanks.:popcorn:

---

### Post by swisscow on 2007-07-09
> **Cool Surfer said:**
> So hiren boot cd also has that feature to take backups-dump backups?
 Sorry - don't understand - what is hiren?

As for the size of the image, partimage only takes the data on the drive, so for example if you have a 20GB partition but only 2GB of data, effectively only the data is shrunk. As for the actual image sizes, my root image is 1.1 GB and home 535MB. I have Kubuntu with a fairly standard install, not too much else. You can also adjust the compression in partimage.

Hope that helps

---

### Post by highenergy on 2007-07-09
Hello,

There is a tool named Ghost For Linux (G4L). You may want to take a look. You don't need hiren.
> 
Ghost for Linux is a hard disk and partition imaging and cloning tool similar to Norton Ghost(c). The created images are optionally compressed and transferred to an FTP server instead of cloning locally.

[ http://sourceforge.net/projects/g4l ]( http://sourceforge.net/projects/g4l )

---

