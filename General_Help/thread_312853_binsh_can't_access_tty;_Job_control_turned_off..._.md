---
title: "/bin/sh: can't access tty; Job control turned off... what have i done now???"
date: 2006-12-05
forum: General Help
---

### Post by shooshu on 2006-12-05
hey. when i turn my computer on, it starts up normally  
         bringing up the ubuntu loading essential drivers.. 
         etc.. and then it continues to load and then it brings 
         up a new screen that is black and has white writing 
         saying

"BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'Help' for a list of built-in commants

/bin/sh: can't access tty; Job control turned off

         and then when i type in 

#help
 
         it brings up

Built-in commands:
------------------
      . : alias bg break cd chdir command continue eval exec 
      exit export false fg getopts hash help jobs kill let local 
      pwd read readonly return set shift times trap true type 
      ulimit umask unalias unset wait [ ash basename busybox cat 
      chmod chroot chvt clear cmp cp cut deallocvt dumpkmap echo 
      egrep env expr false fbset fdflush dgrep grep hostname 
      ifconfig ip kill ln loadfont loadkmap ls mkdir mkfilo 
      mknod mktemp more mount mv openvt printf ps pwd readlink 
      reset rm rmdir sed setkeycodes sh sleep sort stat sync 
      tail tee test touch tr true tty umount uname uniq yes



sooo.... what have i done????/ what can i do???

---

### Post by Iowan on 2006-12-05
I have a Dapper box that seems to have a flakey HD... I leave it on, cuz it has trouble booting.  Occasionally, it gets to the point where it won't run applications.  Then, when I reboot, I get filesystem errors - sometimes it seems to start booting and drops into the same screen you seem to be seeing.  If I retry a few times, it eventually suceeds and works for several days (weeks?), but the writing on my wall sez "get ready to reinstall on another drive".  
... your wall may read differently...

---

### Post by roque86 on 2007-02-21
I have the same problem. In my case, i figure this out editing the file menu.lst (/boot/grub/menu.lst).

May be i had a different problem with only the same debug message, but i could see that this file was corrupted (in my case because a windows installation and grub-install command), and when i edited it the system boot up normally again.

My menu.lst file wants to boot up in (hd0,2) and /dev/hdc3, but the correct for was (hd0,1) /dev/hdc2

Note that the grub report errors in this situation, but if we have (hd0,1) /dev/hdc3 it will boot up with error (booting swap partition? rsrsrs, i don't know)

---

