---
title: "Allocating space from dev/sda3 to system file"
date: 2013-04-01
forum: General Help
---

### Post by ricardoojm on 2013-04-01
Hi all,
I installed ubuntu firstly in a 18GB partition (in the other partition windows is installed). Afterwards, I realized that I needed more space in order to run some stuff, then I allocated some more space from the windows partition to the ubuntu partition (using the disk manager in windows). The problem is that now there is an incoherence when I check the size of my ubuntu partition.

When I just open the home folder and check the size of the file system, it says that it has only the previous 18GB. The same happens when I run the command "df -h". Here is the output of it:

Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       18G   13G  4.0G  76% /
udev              3.9G  4.0K  3.9G   1% /dev
tmpfs             1.6G  896K  1.6G   1% /run
none              5.0M     0  5.0M   0% /run/lock
none              3.9G  156K  3.9G   1% /run/shm
/dev/sda3        88G   19G   70G  21% /host
/dev/sda2       145G   99G   47G  68% /media/52D49400D493E48F

The other space I allocated using windows went to the dev/sda3. So, is it really right (as I am a very beginner, I might be talking rubish...)? I am trying some analysis in Matlab, and they save very large files in the tmp/ folder. Once the analysis are still not working, I assume that the 88G in the dev/sda3 are not acessible.

So, how can I move the 88GB from dev/sda3 to the file system?

I would really appreciate any help.
Best wishes,
Ricardo

---

### Post by Impavidus on 2013-04-01
Hello Ricardo,
> **ricardoojm said:**
> 
/dev/loop0       18G   13G  4.0G  76% /
This tells me you have a wubi install. The wubi install uses a virtual partition existing inside your /dev/sda3 partition. The 19GB used on /dev/sda3 is exactly the virtual partition + the swap space. You can make the wubi install larger using these instructions: [https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk)
The limit is 30GB.

Assuming you want 88GB (the size of the entire /dev/sda3 partition), you'll have to migrate your wubi install to a partition of its own (see [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)). Alternatively, and the cleaner way as I don't really know whether you can migrate a wubi install to a partition of its own which is the same as the partition where wubi was, make backups of your files on an external drive and reinstall ubuntu, now as a proper dual boot. Also make backups of your windows files. They should be save, but if you do anything wrong you can lose them. Then boot Ubuntu from the install medium and install it. Read [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) and [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) for some help or ask questions here.

Cheers, Impavidus

---

### Post by ricardoojm on 2013-04-06
Hi
Thanks a lot.
I decided to leave the wubi install :)

Cheers!
Ricardo

---

