---
title: "Ubuntu Startup Freezes at Purple Screen"
date: 2013-01-16
forum: General Help
---

### Post by smunson on 2013-01-16
So I found out today that I would need a few things downloaded in Ubuntu for a class I'm taking. One of those being VMPlayer. 

I downloaded and installed it, and attempted to create a virtual box of a Windows 7 OS with the OS disc I had. I got to the point where it was installing and expanding windows files to about 13% and during this time it was very slow going, and then at some point it froze completely and I was forced to hold the power button and force quit.

When I attempted to reboot Ubuntu, it gave a quick error about a prefix not being set (this is all I could read as it popped up quickly and then went to the purple screen) and then froze.

At this point I've attempted to reboot about a dozen times and it just freezes at the purple screen before login every time.

Help is appreciated. I understand if there is no quick solution to this, as I have no clue what to do from here.

Thanks.

---

### Post by oldfred on 2013-01-17
Welcome to the forums.

You should always remember the elephants when forcing a shutdown, otherwise file system may be damaged and need e2fsck.

       Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
    
       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

