---
title: "Need help GRUB Is not leting me into vista It reboots itself."
date: 2007-11-20
forum: General Help
---

### Post by maddog_326 on 2007-11-20
When Grub loads You see Ubuntu is working fine but when I choose vista/longhorn The computer only will load Ubuntu but not vista Please help.And yes I did not remove my NTFS file partition. I'm lost this is on my dads computer but mine works fine.

---

### Post by bettlebrox on 2007-11-21
Sounds like grub might have the wrong partition set for the Windows partition.

Look at the file /boot/grub/menu.lst . The last few line should look something like this:

[INDENT]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Professional
root            (hd0,1)
savedefault
makeactive
chainloader     +1[/INDENT]


Make sure this line:
[INDENT]root            (hd0,1)[/INDENT]
is correct for your system. Now this is going to get a little confusing! 8D

hd0 means the 1st hard-drive
1 means the *second* partition. 

(Counting starts at 0 instead of 1.) So it means my grub boots windows from the first hard drive on my system and from the second partition. 

So boot into Ubuntu and start the *Partition Editor* tool, it's under System->Administration. And see what location your NTFS filesystem for Windows occupies on your disk.

---

### Post by maddog_326 on 2007-11-21
Thanks for the help but he already wiped the hard drive and reinstalled windows vista. it's working fine now to bad he had to get rid of Ubuntu:(

---

### Post by hikaricore on 2007-11-21
I hate to see people react hastily in situations like this, considering there are several threads and other resources on fixing the issues Vista causes /w Grub. :/

---

