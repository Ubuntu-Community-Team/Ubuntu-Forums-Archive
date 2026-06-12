---
title: "Installation of 2nd m.2 ssd"
date: 2023-07-02
forum: General Help
---

### Post by Old Jimma on 2023-07-02
Hello Ubuntuers:

I want to install a 2nd m.2 SSD in my laptop, and would appreciate your commenting on the multi-step method I'll use. Here it is:

[LIST=1]
[*]Open the case, remove the screw from the 2nd m.2 ssd bay, install the m.2 ssd, replace the screw.  Close the case.
[*] Reboot.
[*]Create mountpoint: **sudo mkdir /mnt/WD1**
[*]Give the account owner ownership of the mountpoint: **sudo chown -R ownderusername:ownderusername /mnt/WD1**
[*]Allow read, write, and execute privileges for the user at the mount point: **chmod -R 777 /mnt/WD1**
[*]add the following lines to /etc/fstab
> **UUID=6b1e17d8-94af-4570-89cb-eddece14952c /mnt/WD1 ext4 defaults,nofail,discard,noatime 0 2**
 where 6b1e17d8-94af-4570-89cb-eddece14952c is the UUID determined from the blkid bash command.


[/LIST]

Please let me know if this seems correct. 

Thank you,
Old Jimma from the Old Country

---

### Post by TheFu on 2023-07-02
This thread is a duplicate of the 1 yesterday. **What start a new thread?**

As noted in the other thread - you shouldn't worry about permissions until after the file system is mounted.  Also, you left out the part were you partition and put at least 1 file system onto the new storage.  Looks like you intend for ext4 to be used, but never use **mkfs** to lay that file system down.

According to the file system hierarchy standards, /mnt/ should only be used for temporary mounts, like when an admin needs a place to work, move files around, etc.  It shouldn't be permanent.

Also, UUIDs are a pain.  Label the file system (I'd use gparted), then use LABEL= rather than UUID= in the fstab.  I use UUIDs only for EFI and /boot.

Based on the permissions/chmod shown, you realize that only this userid will have access.  You really shouldn't use 777 for permissions. please erase that idea from your mind forever.  775 would be minimal security.

Also, the last number in the fstab should be a 2, so that **fsck** checks are run from time to time.  I got that wrong in the other thread. Sorry.
man fstab says:
```
       The sixth field (fs_passno).
              This field is used by fsck(8) to determine the order in which filesystem checks are done  at
              boot  time.   The root filesystem should be specified with a fs_passno of 1.  [B]Other filesys&#8208;
              tems should have a fs_passno of 2[/B].  Filesystems within a drive will be checked sequentially,
              but  filesystems on different drives will be checked at the same time to utilize parallelism
              available in the hardware.  Defaults to zero (don't fsck) if not present.
```

I wouldn't bother with the other options in the fstab line. The defaults address everything already.  The noatime isn't well understood. The manpage:
```
       noatime
              Do  not  update  inode  access  times on this filesystem (e.g. for faster access on the news
              spool to speed up news servers).  This works for all inode types (directories  too),  so  it
              implies nodiratime.
```

For data only storage, for better security, you might want to add **nodev** and **nosuid** options, if you want to add some options.  Even **noexec** could be useful, if you never intend to have any programs or scripts there.

It would be easier to just do what you think, show the fstab line, then show the permissions on the mount point and the df -Th for that file system.  Worst case, you'd probably be close enough and might only need 1 or 2 corrective commands.

---

### Post by Old Jimma on 2023-07-03
Hello The Fu:

Please accept my sincere thanks for once again helping me to configure my Ubuntu machine well.

Here is what I did:

[LIST=1]
[*]Open the case, remove the screw from the 2nd m.2 ssd bay, install the m.2 ssd, replace the screw.  Close the case.
[*] Reboot.
[*]Use gparted to format the m.2 as ext4 and using gparted, give the device a label (in this example, WD1)
[*]sudo mkdir /home/WD1
[*]Give the account owner ownership of the mountpoint: sudo chown -R ownderusername:ownderusername /home/WD1
[*]Allow read, write, and execute priveleges for the user at the mount pont: chmod -R 775 /home/WD1
[*] add the following lines to /etc/fstab
> # new m.2 ssd
Label=WD1 /home/WD1 ext4 defaults,nofail,discard,nodev,nosuid,noexec,fsck 0 2

[*] reboot
[/LIST]

When I rebooted, I did not receive any error messages. I checked the ownership of /home/WD1 and it belonged to my user

[LIST]
[*]When I rebooted, I received no error messages,
[*]I checked the /home/WD1  directory and it belongs to ownerusername, and
[*]I checked to sed if the m.2 was mounted in /media or elsewhere: it did  not appear to be. If my observation is correct, when I add data to this new directory, it should not fill up my first m.2 SSD inadvertently and cause an unhappy day.
[*]
[/LIST]

It seems to work, thanks to you TheFu. Let me know if I can buy you a cup of coffee sometime.

And, as always... I'd be greatful (and I'd benefit greatly) from your review and further comments about this procedure.


Thanks to TheFu, I've made progress in mounting my second m.2 drive.

Now, all I have to do is to think of a plan for putting data on it so that i can verify that I'm actually not adding data to my frst m.2 drive inadvertently because the 2nd m.2 drive is still somehow mounted temporarily on the first m.2 drive.


Many thanks,
Old Jimma from the Old Country

---

### Post by TheFu on 2023-07-04
> **Old Jimma said:**
>  
[*]Give the account owner ownership of the mountpoint: sudo chown -R ownderusername:ownderusername /home/WD1
[/LIST]
...
```
# new m.2 ssd
Label=WD1 /home/WD1 ext4 defaults,nofail,[s]discard,[/s]nodev,nosuid,noexec[s],fsck[/s] 0 2 
```


The order of that step is wrong.  Don't chown until after the storage is mounted.  I suspect that your prior attempts already set the owner:group which was carried over, but on a fresh SSD, it won't work.

I'd use this fstab line:
```
Label=WD1 **/d**/WD1 ext4 defaults,nofail,nodev,nosuid,noexec  0 2 
```
I don't think the options I've removed are valid or wanted.
Also, placing storage under /home/ isn't a good idea. There are many reasons why not.  I place extra storage under /d/ myself.  Initially, I started with /d/Data, but quickly outgrew that and added a /d/D2, /d/D3, ... /d/D7.  Over nfs, the mounts look like this:
```
Filesystem                                       Type  Size  Used Avail Use% Mounted on
istar:/d/D1                                      nfs4  3.5T  3.5T   43G  99% /d/D1
istar:/d/D2                                      nfs4  3.6T  3.4T  182G  96% /d/D2
istar:/d/D3                                      nfs4  3.6T  3.6T   45G  99% /d/D3
istar:/d/D6                                      nfs4  3.6T  1.8T  1.7T  53% /d/D6
istar:/d/D7                                      nfs4  3.6T  454G  3.0T  14% /d/D7
```
And for backups, I use /d/b-D1 ... /d/b-D7. No need to get too fancy.  Backup storage is USB3 connected. All other storage is SAS, SATA or eSATA connected.
I didn't show the local mounts of those file systems because I use LVM and fear the device names would confuse people.

---

