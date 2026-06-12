---
title: "Delete freezes Konqueror"
date: 2007-12-08
forum: General Help
---

### Post by Tosa on 2007-12-08
I have this strange (read annoying) problem that started after I'd installed some updates yesterday. Yes, I was stupid enough not to pay much of attention what it was. Most of the files were ext2(3?) libraries.

The problem now is that if I try to delete something in Konqueror it freezes during the process. Trying to empty Trash stops along the way too. The funny thing is that I had Firefox opened and it froze also. Some other opened programs weren't affected.

After reboot I opened Konqueror only and deleting worked. Then I started Firefox and got stuck again when I tried to empty trash.
Now I really feel frustrated. I have to reboot to delete something?!

Anyway did someone experience similar problems after the update?

TIA

---

### Post by Tosa on 2007-12-09
I think I've figured it out... Maybe this will help someone with similar problem.

Since it was obviously related to hard drives I thought I'd check fstab, just in case, not that I thought I'd really find something there. But actually I did. Hard drives were all mixed up. My boot drive used to be sda, now it was sdc... But my second data drive remained sdc!
I've rewritten fstab and now everything seems to work fine (knock on wood).

I've looked around some more and found that problems with hard drives being mixed up upon reboot were already reported. I've installed the second data (SATA) drive after installing gutsy, so I had to put it in fstab myself. I assigned it as /dev/sdc1, while  my other drives (ATA, SATA) were asigned as UUID=*, and that seems to be the cause of the problem.

In another thread I found this link [https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID) 
and assigned an UUID. So I should now reboot and hopefully everything will work as it should...

---

