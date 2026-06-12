---
title: "Bad blocks on an encrypted LVM partition"
date: 2012-12-04
forum: General Help
---

### Post by tk83 on 2012-12-04
I have my desktop PC Ubuntu installation on an encrypted LVM partition:
```
/dev/sda1 ntfs Windows
/dev/sda2 ntfs Windows
/dev/sda3 ext4 /boot
/dev/sda4 LUKS (encrypted)
           dm-0 (encrypted device) LVM PV
                        MainVG (volume group) 
                                                   -> root
                                                   -> swap
                                                   -> home
```In the syslog on this machine I saw some sense key errors from sda. As luck would have it there are bad blocks on the sda4 partition:
```
kubuntu@kubuntu:~$ sudo badblocks -nsv /dev/sda4 
Checking for bad blocks in non-destructive read-write mode
From block 0 to 281341951
Checking for bad blocks (non-destructive read-write test)
Testing with random pattern: 10796512done, 5:51 elapsed. (0/0/0 errors)
.....
done                                                 
Pass completed, 8 bad blocks found. (8/0/0 errors)
```I've looked at the badblock HOWTO but the procedure looks too long and complex to be worth the time due to this machine using both LUKS and LVM. 

We recently moved house and (despite packing carefully) I reckon these bad  blocks were caused by jolts during transport. Is it likely that the drive is completely wrecked and should be  replaced or should I wipe it and re-install using 'check for bad blocks' on the partitioner during installation?

---

### Post by Herman on 2012-12-04
I'd be making backups more frequently than normal just to be sure.

You could try using the e2fsck command for coping with bad blocks within the file system itself,  according to the man page it says to type the -c option twice. I'm not sure if they mean -c -c, or if they mean -cc.
Something like, sudo e2fsck -c -c -k -v /dev/<file system> should work.
Then check for bad blocks again after some use and see if it the badblocks continue to appear.

---

