---
title: "Mount Points For Data Disks"
date: 2017-07-05
forum: General Help
---

### Post by scpatl4now on 2017-07-05
I have used Ubuntu for a long time and generally dont care to mess with where secondary disks are mounted.  That said, I recently built a new desktop with a Ryzen 1700+ CPU so I went with 17.04 for better Ryzen support.  My problem has been the I have 1 disk that has the system and home (separate partitions), and 2 fixed drives.  I always assumes extra drives were mounted under /media (I also have a large USB drive that I had an unfortunate formatting accident with unplugged which I would have assumed would mount there).  My problem is that they didnt end up there but at /media/(my username) which caused me some confusion when I was recovering files from the USB drive.  I have since just decided to mount the extra drives at /mnt instead (since that sounds more logical to me).  I have read that /mnt is for temporary mount points.  Am I going to run into problems later because of this?  Also, why did the disks mount to /media/(username)?

---

### Post by The Cog on 2017-07-05
> new desktop with a Ryzen 1700+ CPU
Sweet!

I believe that /mnt is the normal home for permanent drives, and /media/username is for removable media like CDs and USB drives. My choice would be to put the drives in /etc/fstab (one entry per partition you want to mount). THis should prevent them being treated like removable media. Use UUID notation to identify the disk, not the device file name which can in theory change from boot to boot. Use 0 2 for the last two numbers.

I think it's a privacy thing: it prevents users even seeing the volume names of the media that other users have mounted.

---

### Post by scpatl4now on 2017-07-05
Thanks for the reply.  Thats what I ended up doing.  I used /mnt and updated fstab.  Why 0 2 in the last numbers?  I think I have 0 0
(also video that was taking me 1 hour to encode is now taking 10 mins....THATS SWEET!)

---

### Post by ajgreeny on 2017-07-05
Ubuntu has used **/media/username** as the mountpoint for any inserted USB drives, or internal drives not mounted at boot by fstab, for some time now; I can't remember when it changed from /media but now you know it should not present you with any problems.

You are correct, however, in suggesting that other disks or data partitions are probably better mounted in /mnt using /etc/fstab; this is how I have done this for a long time.

I suggest you give all the partitions on all your disks a label eg, data1, data2, etc etc, and then you can create a separate mountpoint folder for them all using the label name for each partition with ```
sudo mkdir /mnt/data1 /mnt/data2
```and so on.
If those partitions are formatted to ext# filesystems you will also need to take ownership of the folders with ```
sudo chown -R username:username /mnt/data1 /mnt/data2
``` to make them and the files in them read/write for you as user.

---

### Post by oldfred on 2017-07-05
My old BIOS system would mount a flash drive at sdf, as I had several drives, but if I rebooted with flash drive plugged in, it became sdb and every other drive moved up a letter.
My newer UEFI system did something similar in that second drive was sdb, but DVD was in middle so grub & some of my boot command saw it as hd2 when it should be hd1. DVD was hd1 at time of boot.
I found it was critical to use SATA ports in order and make sure drives are at first SATA port or SATA0. Not sure with new NVMe drives and SATA how drive order may be.

Also links to the details on creating mount point like /mnt/data, giving yourself ownership & permissions, and editing fstab to add entry to permanently mount a partition. Some partitions I do not always mount, so I label those, so at least when automounted they have a label of what they are.
       The actual user settings are small. My /home is 2GB with most of that as .wine' Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home in my typical 25GB / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives. 
   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /mnt/data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /mnt/data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by scpatl4now on 2017-07-05
I've always found that having /home and / on separate partitions was easier for me to keep up with especially if I have to reinstall.  Installing 17.04 on my new system was a nightmare with UEFI so I used BIOS without issue.  I always get confused over mount points and syslinks, but the reason I just used /mnt and put it in fstab was that I had problems sharing files on those disks with another desktop (16.04).  Once I changed the mount points in fstab everything worked.  I was just concerned that /mnt wasnt correct but I now know its more a matter of ones preference than anything (and that doesnt make my head explode)

---

### Post by The Cog on 2017-07-05
> Why 0 2 in the last numbers?
[https://en.wikipedia.org/wiki/Fstab](https://en.wikipedia.org/wiki/Fstab)
Several drives can be numbered pass 2 - I believe pass can only be 0, 1, 2.

---

### Post by oldfred on 2017-07-05
See also:
man fstab

>        The fifth field (fs_freq).
              This field is used by dump(8)  to  determine  which  filesystems
              need  to  be  dumped.   Defaults  to  zero  (don't  dump) if not
              present.

       The sixth field (fs_passno).
              This field is used by fsck(8) to determine the  order  in  which
              filesystem  checks  are  done at boot time.  The root filesystem
              should be specified with a fs_passno of  1.   Other  filesystems
              should  have  a fs_passno of 2.  Filesystems within a drive will
              be checked sequentially, but  filesystems  on  different  drives
              will  be  checked at the same time to utilize parallelism avail&#8208;
              able in the hardware.  Defaults to  zero  (don't  fsck)  if  not
              present.



The fsck only is for the ext2, ext3, ext4 family of formats, so use 0 for any other formatted partition on 6th field, as you cannot run fsck anyway.

---

