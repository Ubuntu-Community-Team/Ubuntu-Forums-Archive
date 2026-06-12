---
title: "Increase /boot space using lvm 16.04LTS"
date: 2019-11-21
forum: General Help
---

### Post by Frank P on 2019-11-21
Attempting to increase size of boot partition.  
Trying to follow Digital Ocean tutorial: [FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]How To Use LVM To Manage Storage Devices on Ubuntu 16.04LTS[/FONT]
It looks like only 3gb out of 145gb are in use
I tried the command below and it errored.
[LEFT][COLOR=#222222][FONT=Verdana]Since /boot isn't a logical partition do I have to create one from it?[/FONT][/COLOR][/LEFT]
 

[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]sudo lvresize -L +5G --resizefs vostro1310-vg/root
[/FONT]error message: [FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]Insufficient free space: 1280 extents needed, but only 7 available


[/FONT]

---

### Post by TheFu on 2019-11-21
In ubuntu installs, /boot usually isn't managed by LVM.  It is usually a straight ext2 file system on a primary partition. That means lvresize won't work.  Here's my 16.04 system.

```
$ lsblk -o name,size,type,fstype,mountpoint
NAME                        SIZE TYPE  FSTYPE      MOUNTPOINT
sda                       465.8G disk      
+-sda2                      732M part  ext2        /boot
+-sda3                    464.6G part  crypto_LUKS      
| +-sda3_crypt            464.6G crypt LVM2_member      
|   +-ubuntu--vg-root        25G lvm   ext4        /
|   +-ubuntu--vg-stuff      100G lvm   ext4        /stuff
|   +-ubuntu--vg-swap_1     4.1G lvm   swap        [SWAP]
|   +-ubuntu--vg-home--lv    75G lvm   ext4        /home
+-sda1                      512M part  vfat        /boot/efi
```
Only the lines with "ubuntu--vg" are using LVM under the sda3_crypt LVM container.
There is 260.08G free in the VG, but that doesn't help make /boot (sda2) any larger. It isn't in the VG and with 16.04, it cannot be.

---

### Post by Frank P on 2019-11-21
Okay, my /boot is not in an lvm group
I think I've seen some other (rather scary :-) ) ways of increasing a partition size.
What would you recommend
Thanks
Frank

---

### Post by TheFu on 2019-11-21
> **Frank P said:**
> Okay, my /boot is not in an lvm group
I think I've seen some other (rather scary :-) ) ways of increasing a partition size.
What would you recommend


Reinstall. This time make the /boot larger.  Restore using your backups.  If your backups don't support doing that in 30-45min, you need better backups.

Need some facts unless you want wild guess answers.  Those can be fun and dangerous.

But there might be other ways. If some data were provided, someone might be able to help.  Maybe run the command I did above and post the output for the system?

The output from **parted -l** and **df -hT -x squashfs -x tmpfs -x devtmpfs **would be good too.  

Code tags, please.

---

### Post by Frank P on 2019-11-22
```

[LEFT][COLOR=#000000][FONT=Ubuntubeta]Reinstall. This time make the /boot larger.  Restore using your backups.  If your backups don't support doing that in 30-45min, you need better backups.[/FONT][/COLOR][/LEFT]

```
I'd like to clarify your first response before considering other alternatives.
I'm open to reinstalling but it gives rise to a further question. I've got data backups I can restore but not configuration files but I can recreate those. But since /boot doesn't end up as lvm partition
won't I end up with the same problem. I've never used anything except the default lvm settings so maybe I'm missing something.
Thanks
Frank

---

### Post by TheFu on 2019-11-22
I've requested the output from 3 commands.  Please.
Need some facts.

---

### Post by Frank P on 2019-11-23
sorry for the delay - missed your response. You said 3 commands but I only see request for 2.

[FONT=Verdana]sudo parted -l[/FONT]
```

[FONT=Verdana]Model: ATA WDC WD1600BEVT-7 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: [/FONT]
[FONT=Verdana]Number  Start   End    Size   Type      File system  Flags
 1      1049kB  512MB  511MB  primary   ext2         boot
 2      513MB   160GB  160GB  extended
 5      513MB   160GB  160GB  logical                lvm[/FONT]
[FONT=Verdana]
Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vostro1310--vg-swap_1: 1023MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: [/FONT]
[FONT=Verdana]Number  Start  End     Size    File system     Flags
 1      0.00B  1023MB  1023MB  linux-swap(v1)[/FONT]
[FONT=Verdana]
Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vostro1310--vg-root: 158GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: [/FONT]
[FONT=Verdana]Number  Start  End    Size   File system  Flags
 1      0.00B  158GB  158GB  ext4[/FONT]


```

[LEFT][COLOR=#000000][FONT=Verdana][FONT=Verdana] sudo df -hT -x squashfs -x tmpfs -x devtmpfs
[/FONT][/FONT][/COLOR][/LEFT]
```

[FONT=Verdana]Filesystem                      Type  Size  Used Avail Use% Mounted on
/dev/mapper/vostro1310--vg-root ext4  146G  3.1G  135G   3% /
/dev/sda1                       ext2  472M  161M  288M  36% /boot [/FONT]

```

Obviously this pc - test server, doesn't need any more /boot space but I want to make sure I can change it on this server without messing up before I try it on the live one.
Thanks
Frank

---

### Post by TheFu on 2019-11-24
A wild guess.  Run this:
```
sudo apt autoremove
```
If the package manager isn't too screwed, that will clean up /boot/ ... most likely.  Old kernels need to be cleaned up. Some package management tools do it automatically. Some require manually running that every few weeks.
500MB is enough for 6-8 kernels usually. I have 3 kernels installed using 186M.

Perhaps I'm misunderstanding how showing the output from a completely different computer will help solve the issue? Can you please explain?

---

### Post by Frank P on 2019-11-24
I'll try.

History: 
I've had the same problem previously and after several tries at fixing it I had to do a clean install. .
[LEFT][COLOR=#222222][FONT=Verdana]I run sudo apt autoremove frequently[/FONT][/COLOR][/LEFT]
This time I figure if I can't increase the boot size on a healthy system there's no point even trying on one with problems.
So if I get the /boot size increased on the test server I'll try to fix the problem one; otherwise I'll just do a clean install and reload the backups.
Does that make sense?
Thanks
Frank

---

### Post by TheFu on 2019-11-24
And how does that output help anyone to help you?

Good luck to you.

---

### Post by Frank P on 2019-11-24
I think you've misunderstood me or maybe I wasn't clear. 
I just want to know if it's possible to increase the size of the boot partion on a 16.04LTS sever
If it is - where can I find the steps
If it isn't - I'll reinstall
Thanks
Frank

---

### Post by aljames2 on 2019-11-24
What you are asking is not a simple procedure after installation is done  especially if your drive has no more room to accommodate a larger /boot  partition.  Most users when they set up their drive on original  installation will allocate some amount to /boot, and then (incorrectly  so) allocate & format their remaining space to the LVM ext4  filesystem.  This essentially renders your drive full with no room for  boundary partitions to be expanded...even though you have not yet used  up all the LVM space with data.  The magic of LVM is to start out small and expand  as needed.  If this is at all similar to what you have, then the /boot cannot be  increased until the LVM filesystem is first downsized and then the LVM  partition reduced.  This is complicated, very risky to data loss and  cannot be done on a running system (requires USB or CD boot, etc.).   Then once the LVM is reduced, a tool like gparted or parted is used to  increase the /boot partition.

All this being said, as TheFu  already stated, reliable backups and a fresh installation is much easier  & more likely to succeed.

As for maintaining a 500MB /boot...

My /boot right now is this, with 5 kernels in it from updates (as you can see I'm running a 500MB /boot on sda2):
```

/dev/mapper/LVG-root                     ext4       23G  4.1G   18G  19% /
/dev/sda2                                ext2      462M  281M  158M  65% /boot
/dev/sda1                                vfat      549M  6.1M  543M   2% /boot/efi
/dev/mapper/WD--vg2--bak-lv_serverOS_bak ext4      393G  4.2G  385G   2% /media/WD3tbHDD2/backup-serverOS
/dev/mapper/WD--vg2--bak-lv_data_bak     ext4      503G   73M  498G   1% /media/WD3tbHDD2/backup-data

```

Then...after apt autoremove that I just ran 5 seconds ago, it is this:
```

/dev/mapper/LVG-root                     ext4       23G  3.3G   19G  16% /
/dev/sda2                                ext2      462M  146M  293M  34% /boot
/dev/sda1                                vfat      549M  6.1M  543M   2% /boot/efi
/dev/mapper/WD--vg2--bak-lv_serverOS_bak ext4      393G  4.2G  385G   2% /media/WD3tbHDD2/backup-serverOS
/dev/mapper/WD--vg2--bak-lv_data_bak     ext4      503G   73M  498G   1% /media/WD3tbHDD2/backup-data

```

If the apt autoremove is not helping you then this is likely not normal and a fresh install would still be in order.  Backup first!  Good luck

---

### Post by Frank P on 2019-11-24
Okay, I think I understand it now. 
sudo apt autoremove failed
So I'll go the fresh install route, with 18.04 LTS,  and make sure I have a larger boot partition before I reload the backups
Thanks
Frank

---

