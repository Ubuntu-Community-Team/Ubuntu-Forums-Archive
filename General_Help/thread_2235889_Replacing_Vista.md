---
title: "Replacing Vista"
date: 2014-07-23
forum: General Help
---

### Post by anon_private on 2014-07-23
If I replaced Vista with Ubuntu 12.04.2 and later decided that I prefer Vista, could I simply re-install Vista and automatically delete Ubuntu, or would I have a problem?

Thanks

Ps. Not interested in dual boot

---

### Post by sudodus on 2014-07-23
If you have installation media (I don't remember if it is a CD or DVD disk) for Vista, it is OK. You can make a recovery disk (DVD), and you can make a cloned image of the whole drive. There are several options. The best thing is to ***test that the backup or installation /recovery disk really works*** (test installing into another drive, not overwriting what you have).

Windows would be happy to overwrite whatever is on the drive, but let us hope that you will stay with Ubuntu :-)

---

### Post by oldfred on 2014-07-23
The Windows installer may not see drive if fully formatted for Linux. But if you delete Linux partitions and create a NTFS primary partition with the boot flag then it will install without issue.

       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

            [http://clonezilla.org/](http://clonezilla.org/)
fsarchiver
[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

---

### Post by Mark Phelps on 2014-07-23
Couple of points to consider BEFORE you remove Vista ...

1) Make sure the media you have will fully install/reinstall Vista.  PCs back then often came with a disk, but it was nearly always a CD, and that could NOT be used to reinstall Vista, only to repair it.  So, use this CD on another machine and ensure it takes you to a menu that will allow you to install it.  IF it's only a Repair CD, you will not be able to use it to reinstall Vista.

2) Backups -- a more surefire way to be able to reinstall Vista is to install Macrium Reflect free edition and use it to image off the Vista install to an external drive.  You can also do this to DVDs but that's cumbersome and restoring from those is a lot of work.  Also, be sure to exercise the option to create and burn the Linux Boot CD.  This is a CD that Macrium formats and will allow you to boot into Macrium to run a restore.

---

### Post by gilligan216 on 2014-07-23
if the microsoft windows vista was authenticated to you, and you have the authentication passcode, then call the microsoft 800 number. speak to an operator, get a live download from microsoft.

---

### Post by anon_private on 2014-07-24
> **sudodus said:**
> If you have installation media (I don't remember if it is a CD or DVD disk) for Vista, it is OK. You can make a recovery disk (DVD), and you can make a cloned image of the whole drive. There are several options. The best thing is to ***test that the backup or installation /recovery disk really works*** (test installing into another drive, not overwriting what you have).

Windows would be happy to overwrite whatever is on the drive, but let us hope that you will stay with Ubuntu :-)

Thank you.

I have the Dell/Vista installation disk.

I assume that simply putting this disk in the drive and installing would replace any OS on the drive.

---

### Post by sudodus on 2014-07-24
> **oldfred said:**
> The Windows installer may not see drive if fully formatted for Linux. But if you delete Linux partitions and create a NTFS primary partition with the boot flag then it will install without issue.

       ...

> **anon_private said:**
> Thank you.

I have the Dell/Vista installation disk.

I assume that simply putting this disk in the drive and installing would replace any OS on the drive.

Yes, I think so, otherwise delete the linux partitions according to *oldfred*'s advice.

---

