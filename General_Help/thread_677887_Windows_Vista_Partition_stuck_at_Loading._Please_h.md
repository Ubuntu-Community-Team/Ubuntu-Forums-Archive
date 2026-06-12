---
title: "Windows Vista Partition stuck at Loading. Please help!!"
date: 2008-01-25
forum: General Help
---

### Post by cpow85 on 2008-01-25
Okay so I'm having a problem with my windows/ubuntu box and I havent found a solution yet. I recently installed Ubuntu 7.10 on a separate partition on my vista PC. I used vista's partitioning software to make a partition for Ubuntu and that worked fine. Ubuntu also installed and everything worked fine; in fact, i could load windows from GRUB when i first installed Ubuntu.

Recently; however, i played around with how Ubuntu mounts the windows partition. I wanted the vista partition to always be mounted; so I changed the partition's name and where it gets mounted (in Ubuntu) so it was always mounted at startup. I did this mainly so i could play music and access files from the windows partition without having to mount it every time i started the comp. I mostly did this by messing around with the /etc/fstab file.

Unfortunately i didn't back up the fstab file and now i believe this is where my problem is stemming from. Right now in GRUB if i choose to load windows, it goes to the loading screen and just hangs there. The little bar rolls across and just keeps rolling back and forth. 

I can see the files from Ubuntu in my windows partition so i know the partition isnt compromised; but its just not booting.

I tried a lot of the solutions but none of them worked. I tried fixing the MBR of windows, I used superGRUB and messed around with that and nothing worked. I also have a windows CD; however, That doesnt load either!

I'm not sure exactly what to do now, i cant run fixmbr or fixboot from my windows CD because the windows CD doesnt load (in hangs in the same fasion as the partition does). Im all out of ideas and i havent seen any other solutions than the ones I've tried.

I'm not at my comp right now so i cant run fdisk -l but i will later if need be. Any help would be greatly appreciated!!

---

### Post by ajgreeny on 2008-01-25
I don't think editing the fstab file would affect your ability to run from the windows CD, so I believe you can probably discount that.  I wonder if somehow the UUID of the partition has been changed by your name change, but again I don't think the edit of fstab would do that, and it certainly shouldn't affect the windows CD booting.  It may, however be worth trying to change the fstab again, simply removing the reference to UUID and replacing it with the /dev/hda1 address (may be different on your machine, see the line in fstab immediately above the windows entry) that used to be used in previous versions of ubuntu, and still works OK.  Remember, this time BACKUP! first.

Are you sure you didn't do anything else that may have physically upset the windows partition, as it sounds as if you may inadvertently done so?  Think hard and also try to remember the changes you made to the fstab file.  Don't forget also thet you can sort out the mounting of ntfs file systems using ntfs3g, which on my system was there at install, and mounted the partitions at boot time by default.  If not in your case, go to Applications>System tools>NTFS Configuration Tool and set everything up from there.

---

