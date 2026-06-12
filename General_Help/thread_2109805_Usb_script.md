---
title: "Usb script"
date: 2013-01-28
forum: General Help
---

### Post by NathanMartins on 2013-01-28
Okay I literally pulling my hair out, Iv´e tried almost everything, can´t get it to work. First lets get you guys up to speed, I work at a company that I´m constantly running around fixing things, with the help of my trusty USB drive, well most of the time I have most of my files and tools on it and on my server,  so until that point okay, well ever since I started Linux about a year and a half ago, I saw a few shell scripts that could automate a few things I even made a few to install some things on some local machines, but my point is every time I get to my machine I mostly have to backup and copy pretty much most of my USB to my Pc because most of time I have a few reports and what nots that I got from the other computers. So my point being dose any one have or knows hows of a script that when i run it will copy all the contents of a flash drive to a folder on my machine, if possible running on the background would be nice also. 

-Thanks

---

### Post by oldfred on 2013-01-28
Modify a typical backup rsync script with your from & to locations?

       Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh

    
       [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
    
       Some more examples:
[http://rsync.samba.org/examples.html](http://rsync.samba.org/examples.html)

   Backup to external with check of mounted & email
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)

   rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)
Check for mount of backup partition
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
#[http://ubuntuforums.org/showthread.php?t=1555647&page=4](http://ubuntuforums.org/showthread.php?t=1555647&page=4)
more scripts:
[http://ubuntuforums.org/showthread.php?t=1319155](http://ubuntuforums.org/showthread.php?t=1319155)

---

### Post by NathanMartins on 2013-01-28
Thanks :)

---

