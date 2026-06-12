---
title: "booting into bios setup"
date: 2018-09-04
forum: General Help
---

### Post by jgw on 2018-09-04
I am booting into the bios setup screen.  I was messing with the grub customizer and choose to do system setup.  Now, whenever I boot I get the bios setup.  I was trying to get to the menu that would allow me to run fsck if I am re-booting after I pressed the power off key after a system freeze.  I guess that choosing setup system was a really bad choice.

I can, however, get to the [grub] query, with the esc key, so I need to know a command that will get me back my desktop so I can get into the customizer and fix my mess.

My bios, incidentally, give me some boot options as well.  I am not in front of that machine but they go something like:
P hard disk
p uefi hard disk
dvd

Thank you.................

---

### Post by oldfred on 2018-09-04
You may need to boot your live installer.

But can you boot the recovery mode, second line under each kernel.
That should boot to a command line where you can do a total reinstall of grub. You need to know if UEFI or BIOS boot as grub versions are different. 

Almost never press power off, unless nothing else works. That often corrupts file system(s) so then you need chkdsk on NTFS and fsck on all ext4 partitions.
       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is, and S can be before E, but others should be in order
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274) 
    
       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by jgw on 2018-09-04
Oldfred!  Thanks for the reply.

When my machine freezes it is really frozen.  There is no keyboard and there is no mouse - EVERYTHING is frozen.  So my only option is to power down and then up. 

I did, however, fix this problem.  I booted up with the dvd, then went to my main drive and edited grub.cfg directly and changed the default.  

I will mark this one as solved - thanks again!

---

