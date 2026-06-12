---
title: "Cannot access time machine backup on external HDD after switching from OS X to Ubuntu"
date: 2015-02-11
forum: General Help
---

### Post by Brett_Lindenberg on 2015-02-11
Hi,

I apologize in advance if this has already been figured out - I've put a few hours into this and tried many of the solutions found here and on the rest of the web with no success.

My current situation:
- MacBook got water damaged and is no longer able to be powered on
- Swapped out the SSD from the MB into my new ThinkPad (already had an Ubuntu partition on it)
- Have two years worth of backups on a 2 TB Seagate external drive (the entire thing is journaled / used for time machine only, I believe)
- Do not have permission to move/copy files off of the external drive

I have a lot of valuable things on my old drives, both the SSD in this computer and the external HD with my time machine backups. I want to back them up into the cloud so that I can erase this current SSD to give Ubuntu more than 30 gigs, something I can't do until I know for sure that my files are safe.

I've tried everything that I could find online including simple chmod'ing of the disk, running this script to copy from Time machine ([https://gist.github.com/vjt/5183305](https://gist.github.com/vjt/5183305)), and almost anything else that has been suggested, to no avail. I simply don't have permission to copy them, even though the disk has "access" permissions for all users other than original. If I copy a directory using sudo -r cp, it simply creates a locked, 0 byte file at the destination with nothing in it / unable to open it.

If you have faced this problem before or have seen a solution, please reply and help me out. I apologize if some of the things I've said are incorrect, but I am new to Ubuntu (I love it!) and have not faced this problem before. I do not have access to OS X. Bonus points if I am able to change the permissions so that I can directly upload from the external drive to Google Drive / Mega without copying, since I only have 40 GB on this partition and have 300+ GB that I need to back up.

Any help is very much appreciated. Cheers :)

---

### Post by yancek on 2015-02-11
I've never used a mac so can't tell you anything from experience.  You might get some ideas from the link below.  It's strange that you are getting permissions errors since you only need read permission to access, the write permissions are on the device you are copying TO.  Good luck with it.

[http://askubuntu.com/questions/332315/how-to-read-and-write-hfs-journaled-external-hdd-in-ubuntu-without-access-to-os](http://askubuntu.com/questions/332315/how-to-read-and-write-hfs-journaled-external-hdd-in-ubuntu-without-access-to-os)

---

