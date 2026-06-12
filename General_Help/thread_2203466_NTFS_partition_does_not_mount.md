---
title: "NTFS partition does not mount"
date: 2014-02-03
forum: General Help
---

### Post by electricrider on 2014-02-03
I dual boot with Windows 8. It's the same drive only partitioned. My windows 8 wont start up, it hangs at the startup screen. I was thinking I'd transfer all my 300 gigs of data to an external 3.0 USB 3TB hard drive and reinstall windows, then i'd spend a week painstakingly trying to extract my data back into my new windows 8.

The NTFS volume will not mount, it says it's unsafe. I tried to use NTFSprogs to fix the drive but it didn't help. I also tried the instructions here:[http://www.hecticgeek.com/2012/10/make-ntfs-partitions-read-only-in-ubuntu/](http://www.hecticgeek.com/2012/10/make-ntfs-partitions-read-only-in-ubuntu/) but it didn't help. The drive seems to try to mount but then I get an error. 

If you guys don't know any other Linux tools I can try to use to fix the drive, then i'd need to mount it as read only and hope I can transfer the data. 

Do you guys know of other tools to fix the problem  or best way to mount this partition in read only? Thanks. Oh I'm using Zorin 7.1 which is Ubuntu 13.04

---

### Post by jeanjd63 on 2014-02-03
Hello

Did you try :
**sudo  ntfsfix  /dev/sdXY**     where XY represent the ntfs partition wouldn't mount.

Bye

---

### Post by Mark Phelps on 2014-02-03
While "ntfsfix" might work, more likely, it will not.  It only fixes the most trivial of NTFS errors and is not a substitute for windows CHKDSK.

If you can get access to a Windows PC, I would do the following:
1) Download and burn a CD of the ISO file for Minitool Partition Wizard Boot CD
2) Boot your PC from that and see if it allows you to run a Check on the Windows NTFS partition

If that doesn't work, then I suggest you check with a Windows 8 forum (eightforums.com) is a good one, to see what else they might offer, including the possibility of obtaining an ISO image for a Windows 8 Repair CD, which can be used to do startup repair.

---

### Post by ajgreeny on 2014-02-03
Have you disabled fast-boot on your windows 8 system?  I you do not do so it will normally go to a semi-hibernation type of shutdown which can then be impossible to mount in ubuntu as it will be flagged as still in use and unsafe.

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enab...p-in-windows-8]("http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8")
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/...rid-sleep.html]("http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html")
[http://superuser.com/questions/14472...te-w-dual-boot]("http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot")
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials...ndows-8-a.html]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html")
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mo...u-hybrid-boot/]("http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/")
[http://blogs.msdn.com/b/b8/archive/2...windows-8.aspx]("http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx")

---

