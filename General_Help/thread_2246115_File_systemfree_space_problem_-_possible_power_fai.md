---
title: "File system/free space problem - possible power failure"
date: 2014-09-28
forum: General Help
---

### Post by nbpowell on 2014-09-28
Hello, good people of ubuntuforums!

I recently tried to upgrade from 12.04 to 14.04 but unfortunately was left with a non-booting system.  To recover this, I decided to move my home folder to a new partition and do a clean install from scratch.  I was in the throes of migrating my home directory to a separate partition when calamity struck.

I booted from a live USB stick. My 500GB HDD had 2 partitions - root and swap.  I shrank the size of the root partition to create over 200GB free space (home folder for all users 196GB) and created a new partition in the free space
I then used rsync to copy the contents of my home folder to the new partition. I verified the files against the original and deleted the home folder from my root partition.

I then resized partitions again - shrinking the root partition to 64GB (picked fairly arbitrarily!) and enlarged the new home partition to give it the extra 196GB freed by deletion of the original home folder.  As this was going to take some time, I went to brew a cup of Earl Grey :)

On my return, the machine had restarted for reasons unknown and was attempting (failing, of course) to load 12.04 from the HDD.  I reset the PC and booted into USB live. I was not as bad as I feared!  The contents of the home partition are readable in Nautilus.  However, the drive reports only 14GB of free space, claiming usage approximately double what it should be. GParted recognises the partition as 408GB but claims 394GB used.  Any attempts to modify the partitions in any way just result in Gparted immediately closing when you click the tick.
However, df -h returns 
/dev/sda3       size:216G  used:191G   free:14G  used:94% mountpoint:/home
showing the partition to not have been enlarged :\
I ran fsck from a recovery shell on the live USB which found some errors but claimed it had fixed them.  When I booted back up, nothing had changed.

I don't have a big enough spare drive or anywhere near enough cloud space just to back up the data from my readable home partition and reformat the whole drive (even if Gparted were to let me...) and start again

Are there any diagnostics or disc tools that might help me out of this fix?
Regards
Nick

---

