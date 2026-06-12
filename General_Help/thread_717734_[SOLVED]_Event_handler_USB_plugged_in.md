---
title: "[SOLVED] Event handler: USB plugged in?"
date: 2008-03-07
forum: General Help
---

### Post by justleen on 2008-03-07
Hey There Nice People!


As an introduction: I wiped my harddrive, by accident... yet again i should add :)

Im working on a backup script, that will backup some files to USB disk. 
I was thinking of adding the script to the Crontab, and let the script check wether /dev/sdb1 (my usb disk) is available . if so, backup to the disk..

Offcourse, it would be much nicer to have an event handler: if disk is plugged in, backup first.

But.. where would I be able to find this info, wether a disk is plugged in?
There are some options under "removable media" , but not what i want..

edit:  i know the event show up in dmesg, but how can i use this?  no point checking dmesg with cron, thats back to square one..

Any ideas on this??

---

### Post by justleen on 2008-03-07
Solved:

udev is the key...

[http://ubuntuforums.org/showthread.php?t=164902](http://ubuntuforums.org/showthread.php?t=164902)

---

