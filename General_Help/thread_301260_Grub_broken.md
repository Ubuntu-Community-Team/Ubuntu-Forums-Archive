---
title: "Grub broken"
date: 2006-11-16
forum: General Help
---

### Post by spitfirenut on 2006-11-16
I deleted my NTFS data partition under XP this morning to reformat it FAT32.  Problem is that when I did, the problem is, when I did, I broke GRUB.  I couldn't boot winXP or Dapper.  I fixed the MBR under windows and got it booting, but have not been able to get grub to reinstall.  My linux partition is hda6, (hd0,5).  When I go through the grub repair procedure found on the forums it appears to go correctly, but then still tries to boot hd0,6 which is my swap partition.  I tried one suggestion and tried to reinstall without formatting but the installer won't let me continue.  As this is on a laptop, I'd prefer not to install from scratch again, although it didn't take terribly long to get everything working.  Is there a way I can go in at the console and assign /dev/hda6 as /?  Thanks for your help.  
Don

---

### Post by pdub on 2006-11-16
Are you planning to re-install Windows on the FAT32 Partition?

If yes, then re-install Windows then fix Grub.

If not then you can fix Grub as follows:

Boot with the live Ubuntu CD

Open a terminal and type:
```

sudo grub

root (hd0,5)

setup (hd0)

quit
```

Then reboot

---

### Post by UltraSonicSite on 2006-11-16
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

That helped me out =)

---

### Post by spitfirenut on 2006-11-18
Thanks for the replies, folks.  However, neither helped to fix the problem(yet?)  I need to get into the grub documentation and see how it does what it does.  In the meantime, my very inelegant fix was to install again into the partition that I was saving for freeBSD and try to transfer the ndiswrapper and wpasupplicant files over to the new install.  The good news is that when I did that the new installation saw the old installation and it allows me to boot that one instead.  Anyway, I'm back up and running, but with a bandaid.  Thanks again.

Don

---

### Post by nickpaton on 2006-11-18
Hi Don and welcome to the forums.

May I suggest you install Grubed which has a great GUI.

Amongst other things it allows you to change bootup order, and may possibly sort out your problem (no guarantees in this case though!)

[http://ubuntuforums.org/showthread.php?t=228104]("http://ubuntuforums.org/showthread.php?t=228104")

---

