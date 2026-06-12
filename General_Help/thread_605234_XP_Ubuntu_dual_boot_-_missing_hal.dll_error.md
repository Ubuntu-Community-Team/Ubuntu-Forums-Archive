---
title: "XP Ubuntu dual boot - missing hal.dll error"
date: 2007-11-06
forum: General Help
---

### Post by benlacy2112 on 2007-11-06
So I almost had a dual boot setup running about a week ago.  Here's the issue:  I have 4 partitions at this point, on my 250GB hdd: one with a working Windows XP install, a swap partition, my Linux root, and a shared FAT32 partition.  The Windows boot files (ntldr, boot.ini, etc.) are on the shared FAT32 partition.  

I install Gutsy on the root partition, along with Grub.  Nothing ever touches the Windows partition, as far as I can tell.  Gutsy works great.  I love it.  I reboot to get to grub, and when I hit the XP option, I get to the Windows bootloader screen and hit XP...then I get the awesome "...missing or corrupt hal.dll..." error.  I scoured these forums for days, and none of the solutions that are working for other people are working for me.  

First thing I tried was to pop in my XP install CD and expand the hal.dl_ file, then copy it to my Windoze install (d:\windows\system32\).  The file copies.  Great.  When I reboot I get the same error "...missing or corrupt hal.dll..." 

I try to rebuild the bootcfg (bootcfg /rebuild), but it fails.  It tells me to do a chkdsk.  I do a chkdsk /r, and it found and allegedly fixed an error.  Reboot, same hal.dll error.  Fixmbr gets rid of grub, and gets me to the windows bootloader screen, then when I hit xp I get the hal.dll error again. 

I've also edited boot.ini multiple times to try out the different partitions.  But I get the same hal.dll error time every time. 

I'm at a loss, and I've tried everything others have suggested, so I figured it's time to pose the question myself.  Any help would be appreciated from anybody.  Thanks in advance.

Ben

---

### Post by Happy_Man on 2007-11-06
Forgive my ignorance, but why do you have the Windows directory on a) a FAT32 partition (long held to be the worst FS still in use) 
b) not on C:\?

Just a guess, but I think something's wrong with your partition....

---

### Post by benlacy2112 on 2007-11-06
Happy man,

Just the boot files are on the FAT32 partition.  The actual Windows install is on the ntfs partition.  I'm not sure why the boot files are there, but they are, and they worked before I installed Ubuntu.  

Thanks!

P.S.  I'm assuming all of this is Windows' fault, it's gotta be :)

Ben

---

### Post by doppis on 2007-12-26
I am having the same kind of problem but I have windows on a different harddrive, I have also tried bootcfg /rebuild and adding /fastdetect.  I also added it to the grub menu.lst........ omg I can't figure this crap out.

---

