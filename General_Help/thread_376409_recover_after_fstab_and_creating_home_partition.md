---
title: "recover after fstab and creating /home partition"
date: 2007-03-04
forum: General Help
---

### Post by tashazo on 2007-03-04
Hi,
I need help.  I'm living off a live CD right now.
I tried to create a separate /home partition following this guide:
[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

The only thing I did different than the guide is:
-since I had a previously shared fat32 partition, I took that line out of fstab and replaced with the one recommended for the new home partition
-since I had to change partitions around a bit to fit with gparted, I updated my linux swap to its new hda3
-when I was supposed to save, I changed it from /old/etc/fstab to just /etc/fstab, since I thought that needed to be done to have this work, even though it wasn't in the tutorial

After saving fstab that way, nothing was openable again.  I rebooted with live CD and followed their instructions for recovery (bottom part), but since I didn't have enough space left on my main linux partition (all that copying of home!), that failed.
Then I tried to increase the size of the main partition with gparted, which didn't work well (it was mounted), but after 3 tries I think I was able to do it.  But still, when  I try to boot linux normally, it says there's no room left on the drive even to start the gui.
At this point I have no idea what to do - is there a way to backtrack?  Can I erase the duplicate versions of home I have there without actually getting gnome to start?
Can I fix fstab from afar?
pheww.
ANY help appreciated...trust me!!

---

### Post by caldevil on 2007-03-05
I guess you don't need to panic as i guess your system is quite recoverable. First of all try to create some space on /. Boot from the live cd and try to delete a file from the home backup which is not very important or of which you can take backup to a usb stick. Even if you can create 50MB free space on / you would be able to boot normally. If it works you can go on from there.

---

### Post by tashazo on 2007-03-05
That's the thing - how do I access my / files if I'm on the live cd?
Also, I did increase the partition multiple times - after each time it gave an error message that parts could not be done, but when it read the disks again, it looks liked it did resize.  I increased it from 10gb to 12 and then to 13.5gb.  
When I boot, I don't even get the gnome logon screen - only a message that GDM could not make a new authorization entry on the disk...possibly out of disk space.
etc.
I will try again with gparted.
It seems the /recovery steps I took from the guide created extra problems with all the extra copying it did, and the mounting interfered with gparted.
But I don't now how to undo these steps nor erase those extra backup files nor replace fstab and /home to their regular setups...
I also tried to access the partition thru windows and fs-driver --it didnt work either -- it said the drive 'needs recovery'...
Thanks...

---

### Post by tashazo on 2007-03-05
Okay so I'm back to normal (without any mounting or separate home partitions though), and this is what I did to get here:
-retried with gparted on live cd to increase disk space on my main partition, albeit error messages
-logged into gnome with failsafe terminal
-checked disk spaces with "df -l" and "dc -hc --max-depth=1"
-erased all the various of .Trash's with "rm -rf" to make more space
-replaced /home with /home_backup
-replaced /etc/fstab (it was empty!) with fstab_backup
-restarted
all good.
now to try again with the separate home partition, but I think I'll backup first!!! [-o<

---

