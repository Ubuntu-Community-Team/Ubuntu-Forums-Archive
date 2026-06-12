---
title: "Error 17 and ubuntu doesn't see my partitions"
date: 2007-08-05
forum: General Help
---

### Post by elchuppa on 2007-08-05
I recently installed Ubuntu Feiity as a dual boot setup on the same HD as a win x64 install (resized the ntfs partition during ubuntu installation).  Sadly after the install ubuntu worked fine but I could no longer boot windows from grub.  When the windows install was selected from Grub I would get a disk error message (can't remember exactly what it was).  In any case I tried fixmbr and doing a repair windows install without any positive results.  In the end I had to delete the windows partition, recreate a new one, and then reinstall windows x64.  I then used supergrub to reinstall grub and everything seemed fine, as the proper ubuntu and x64 options were available from grub.  Unfortunately now Ubuntu doesn't boot and I just get an Error 17 message. So it looks like first ubuntu hosed my windows partition, and now windows has returned the favor.  

So now I'm wondering if there's a way to fix the Ubuntu partition.  From windows the partition shows up as an unknown partition but from the partition manager (gparted) on the ubuntu live CD my entire disk (sda) shows up as unpartitioned space (when in fact I have two partitions, one holding ubuntu and the other (sda1) formatted ntfs with windows installed on it).  If I run fdisk -l, the only item listed is sdc which is my external usb drive.

any suggestions would be welcome.

thx.

---

### Post by aJayRoo on 2007-08-05
This probably won't help much but... I get grub error 17 when I try to boot my computer with my external hard drive plugged in and switched on. Its a new and unwelcome problem since I replaced the motherboard in my computer! The problem frustrated me for an hour or two until I realised the external hard disk was the cause!

---

### Post by elchuppa on 2007-08-05
thanks for the tip.  No luck though.

---

### Post by nitro_n2o on 2007-08-05
All right.. so no problems.. when you resized your partition you overwrote the MBR "MasterBootRecord" a small cluster in hd needed to find the boot files.. don't get scared it's ok 
the way i'd fix it is: 
boot with windows cd and go into recovery mode, and type FIXMBR it'll ask some question you should answer yes.. i think 
then you'll  loose ubuntu and can no longer boot to it :( sooo follow this to use the ubuntu liveCD to reinstall grub [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
have fun or wait for another post maybe you'll get something easier to fix it :)

---

### Post by elchuppa on 2007-08-05
thanks for the advice, but I think this would apply when windows won't boot. That was my original problem but I resolved it. I am able to boot windows from grub without issue.
 My problem right now is when I select ubuntu from the grub menu I get Error 17.

---

