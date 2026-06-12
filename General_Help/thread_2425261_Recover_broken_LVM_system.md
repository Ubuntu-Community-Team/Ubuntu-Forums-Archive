---
title: "Recover broken LVM system"
date: 2019-08-22
forum: General Help
---

### Post by yeshey on 2019-08-22
(First post, kinda noob, Pls help :sad:)
So I have a rather clunky dual boot between a windows 10 partition and Kubuntu (Ubuntu 19.04 \n \1)) in an LVM, and messed up.
Wanted to allocate some more space to my swap partition, for that I had to shrink the main one, so I ran this command: *[FONT=times new roman][COLOR=#800000]sudo[/COLOR][/FONT]*[FONT=Consolas]*[FONT=times new roman][COLOR=#800000]lvresize[/COLOR][/FONT]**[FONT=times new roman][COLOR=#800000] -L -10GB /dev/mapper/vg0-ext4[/COLOR][/FONT]**[FONT=times new roman][COLOR=#800000]/ [/COLOR][/FONT]*[/FONT], it gave me a warning of potential data loss, but I had a lot of free space and timeshift backups so I ignored it, NOT GOOD, rebooted right after and the worst happened, was met with the GNU Grub (Version 2.02) Terminal.
(After a lot of research), I can use [COLOR=#800000][FONT=times new roman]*ls (*[/FONT][/COLOR]*[FONT=Consolas][COLOR=#800000][FONT=times new roman]lvm[/FONT][/COLOR][/FONT]*[COLOR=#800000][FONT=times new roman]*/vg0-ext4)/*[/FONT][/COLOR] command to view things inside my root folder (including the timeshift folder!), but when I try to boot into it manually, after raining some lines in the terminal I'm met with another "ubuntu terminal" and I'm stuck. 
So I made a live USB stick and booted into that, installed timeshift but I can't mount my vg0-ext4 logical volume, gives me the error:
```
mount: /mnt: wrong fs type, bad option, bad superblock on /dev/mapper/vg0-ext4, missing codepage or helper program, or other error.
```, so timeshift can't restore it!

What should I do? :sad:

[B]Some more information:
[/B]If I run, from the live stick, *[FONT=times new roman][COLOR=#800000]sudo[/COLOR][/FONT]*[FONT=Consolas]*[FONT=times new roman][COLOR=#800000] fsck dev/mapper/[/COLOR][/FONT]**[FONT=times new roman][COLOR=#800000]vg0-ext4[/COLOR][/FONT]*[/FONT], gives me this error:
```
Error writing block 132128812 (Invalid argument).  Ignore error<y>? yes
Error writing block 132120608 (Invalid argument).  Ignore error<y>? yes
Error writing block 131606831 (Invalid argument).  Ignore error<y>? cancelled!
Error writing block 131608458 (Invalid argument).  Ignore error<y>? cancelled!
Error writing block 131608240 (Invalid argument).  Ignore error<y>? cancelled!
```
(...) and goes on like that

The output of *[COLOR=#800000][FONT=Consolas]sudo[/FONT][/COLOR]*[FONT=Consolas]*[COLOR=#800000]fdisk[/COLOR]*[/FONT]*[COLOR=#800000][FONT=Consolas] -l[/FONT][/COLOR]*:
```
Disk /dev/loop0: 1.9 GiB, 1987817472 bytes, 3882456 sectors

Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes



Disk /dev/loop1: 88.5 MiB, 92778496 bytes, 181208 sectors

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes



Disk /dev/loop2: 54.4 MiB, 57069568 bytes, 111464 sectors

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 42.8 MiB, 44879872 bytes, 87656 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 149.9 MiB, 157184000 bytes, 307000 sectors
Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes



Disk /dev/loop5: 4 MiB, 4218880 bytes, 8240 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 14.8 MiB, 15462400 bytes, 30200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes



Disk /dev/loop7: 1008 KiB, 1032192 bytes, 2016 sectors

Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sdb: 149.1 GiB, 160041885696 bytes, 312581808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xde324ff1

Device     Boot Start       End   Sectors  Size Id Type
/dev/sdb1        1985 312575999 312574015  149G  f W95 Ext'd (LBA)
/dev/sdb5        2048 312575999 312573952  149G  7 HPFS/NTFS/exFAT


Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xdcc90a50

Device     Boot     Start        End    Sectors  Size Id Type
/dev/sda1  *         2048    1026047    1024000  500M  7 HPFS/NTFS/exFAT
/dev/sda2         1026048  829401087  828375040  395G  7 HPFS/NTFS/exFAT
/dev/sda3       829401088  860858367   31457280   15G 83 Linux
/dev/sda4       860858368 1953523711 1092665344  521G  7 HPFS/NTFS/exFAT


Disk /dev/sdc: 29.3 GiB, 31457280000 bytes, 61440000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x08f05c50

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdc1  *     2048 61439999 61437952 29.3G  c W95 FAT32 (LBA)


Disk /dev/mapper/vg0-swap: 8 GiB, 8589934592 bytes, 16777216 sectors

Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/vg0-ext4: 502 GiB, 539030978560 bytes, 1052794880 sectors

Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes



Disk /dev/loop8: 3.7 MiB, 3825664 bytes, 7472 sectors
Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes


```

I'm genuinely scared for all my data, if I could at least boot back into windows I'd be already very thankful.
Any help is much appreciated. 
Thanks in advance.

-A noob that messed up.

---

### Post by TheFu on 2019-08-22
Some of the commands above don't make sense.  It appears there is some confusion between directory relative paths and absolute paths. Unix, Linux, OSX, and Windows all work the same with those ideas.

To use LVM from a *Try Ubuntu* boot disk, you'll need to install lvm package, then "activate" any PVs, VGs, and LVs. Run this:
**sudo vgchange -ay**
Then you can run the typical LVM commands to see what you actually have.
```
lsblk # will show an overview of partitions, PVs, and LVs.
sudo pvs
sudo vgs
sudo lvs

```Those will show the summary for PVs, VGs, and LVs.

I'm a little concerned that you don't actually have any LVM based on the lack of *Linux LVM* being shown in the **fdisk -l** output.  It should look something like this:
```
$ sudo fdisk -l

Disk /dev/sda: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: DAFB6918-901C-424D-AB62-6595830C51CD

Device       Start        End    Sectors  Size Type
/dev/sda1     2048       4095       2048    1M Linux filesystem
/dev/sda2     4096    2052095    2048000 1000M Linux filesystem
/dev/sda3  2052096 7814035455 7811983360  3.7T **Linux LVM**

```
Please show the exact command AND relevant output.  Some of the commands in the first post will not work.  Copy/paste them. Do not type.

---

### Post by yeshey on 2019-08-22
Thank you very much for the reply :)
I wouldn't be too surprised if past me had messed up the LVMs set up..
I'm sorry, but I'm not too sure how I'd install a LVM package in this ubuntu live USB.. I ran[FONT=arial narrow][FONT=arial][COLOR=#000000]** sudo apt-get install lvm2**[/COLOR][/FONT][COLOR=#800000], [/COLOR][/FONT]But it said it was already installed, googled it for a bit but couldn't instruct myself... please forgive my ignorance..
I still ran [COLOR=#000000][FONT=arial]**sudo vgchange -ay**[/FONT][/COLOR], which it gave me:
```
ubuntu@ubuntu:~$ sudo vgchange -ay
  2 logical volume(s) in volume group "vg0" now active
```

And the other commands:

**lsblk**
```
ubuntu@ubuntu:~$ lsblk
NAME         MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0          7:0    0   1.9G  1 loop /rofs
loop1          7:1    0  88.5M  1 loop /snap/core/7270
loop2          7:2    0  54.4M  1 loop /snap/core18/1066
loop3          7:3    0  42.8M  1 loop /snap/gtk-common-themes/1313
loop4          7:4    0 149.9M  1 loop /snap/gnome-3-28-1804/67
loop5          7:5    0     4M  1 loop /snap/gnome-calculator/406
loop6          7:6    0  14.8M  1 loop /snap/gnome-characters/296
loop7          7:7    0  1008K  1 loop /snap/gnome-logs/61
loop8          7:8    0   3.7M  1 loop /snap/gnome-system-monitor/100
sda            8:0    0 931.5G  0 disk 
&#9500;&#9472;sda1         8:1    0   500M  0 part 
&#9500;&#9472;sda2         8:2    0   395G  0 part 
&#9500;&#9472;sda3         8:3    0    15G  0 part 
&#9492;&#9472;sda4         8:4    0   521G  0 part 
  &#9500;&#9472;vg0-swap 253:0    0     8G  0 lvm  
  &#9492;&#9472;vg0-ext4 253:1    0   502G  0 lvm  
sdb            8:16   0 149.1G  0 disk 
&#9500;&#9472;sdb1         8:17   0     1K  0 part 
&#9492;&#9472;sdb5         8:21   0   149G  0 part 
sdc            8:32   1  29.3G  0 disk 
&#9492;&#9472;sdc1         8:33   1  29.3G  0 part /cdrom
sr0           11:0    1  1024M  0 rom  


```

**sudo pvs**
```
ubuntu@ubuntu:~$ sudo pvs
  PV         VG  Fmt  Attr PSize    PFree  
  /dev/sda4  vg0 lvm2 a--  <521.02g <11.01g

```

**sudo vgs**
```
ubuntu@ubuntu:~$ sudo vgs
  VG  #PV #LV #SN Attr   VSize    VFree  
  vg0   1   2   0 wz--n- <521.02g <11.01g
```

**sudo lvs**
```
ubuntu@ubuntu:~$ sudo lvs
  LV   VG  Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  ext4 vg0 -wi-a----- 502.01g                                                    
  swap vg0 -wi-a-----   8.00g   
```

(it's dead night here now, I might take a while to get back to you)
Thank you! :KS

---

### Post by yeshey on 2019-08-31
So, well. My Kubuntu went down the drain, managed to boot back into Windows so I'm not totally broken, No point in continuing this thread because I don't have the broken Linux LVM system anymore. Thanks, Mr. "TheFu" for trying to help out! I'll try to be more careful from now on :D

---

### Post by TheFu on 2019-08-31
Sorry, I didn't see this until today.

When using LVM, it is best not to allocate (or leave allocated) the full VG to all LVs.  Only allocate what is needed at the time.
500+G for / is over 10x too large.  25G would be a max for me. I've not used half that amount for the OS and applications.
Then I'd create a separate LV for /home/ and make it about 50G which is still huge.
The swap LV would be 4.1G - I think that is the only correct size for swap regardless of system RAM.  Just don't try to hibernate, but using standby is 100% fine.

So then you'd have 400+G to be used as needed, where needed. No need to allocate it all.

Some installs will allocate 100% of the VG to an LV at install time.  Reduce that to the 25G ASAP.  You can see my other posts here with my layout. I must have posted it 5 times in the last 5 months.  I have a 500G SSD, but only have allocated less than 50% so far. 

With LVM, adding more storage on a running system is about 10 seconds and a good reminder about storage use.  When/if it gets close to being full, this technique should give me 6 months of warning before storage actually runs out.

---

### Post by yeshey on 2019-09-11
Oh hey! Only saw this today. 
hmm
Yes.. YES! That seems to be the wiser way out. ******Sight****** Had to learn it the hard way. So to resize any Logical volumes they still have to be unmounted? Like, when you say "Some installs will allocate 100% of the VG to an LV at install time. Reduce that to the 25G ASAP" I'll still have to do that from a live USB..? 
(Also, it's OK to leave just the / and swap partitions, where the / already has the /home/ and all else, and slowly allocate more memory to it? Even if there are drawbacks to using just one / with everything in it, I think I'd just keep one and not worry about it anymore even because I don't understand them very well, like... What causes the / to run out of memory if not the /home/ folder? Updates..?)
There's also no GUI way to manage LV's is there? I couldn't find one.. I and the terminal don't go along too well.
I I'll be using partitions now, if I leave space unallocated I can still allocate it to a certain partition, Today's tools do a pretty good job at preventing data loss like Gparted. 


Anyways
Thank you for your time[COLOR=#DAD8D2] [/COLOR] :)

---

### Post by TheFu on 2019-09-11
Memory and storage are 2 very different things.  Available storage has very little to do with RAM, unless you use virtual memory, like a swap LV/partition/file.  On Unix-like systems, swap isn't dynamic.

If you use LVM+ext4, then resizing **larger** doesn't require being unmounted. To my knowledge, all other file systems under LVM would require the file system be offline to be resized up or down. Reducing a file system always requires being unmounted.

No GUI tools that I would trust for LVM.  If you use partitions, then you'll need reboot after any modifications.  Basically, everything I said here was a waste of my time.

LVM is for intermediate and advanced Unix people OR people who want the flexibility it provides, but you have to stop thinking "partitions" and start thinking volumes and logical volumes.  Without that mind flexibility, LVM will be wasted.  The best information about each LVM capability is on your machine, in the lvm command manpages.  You'll need to read those or it is easy to miss adding important options to commands.

---

### Post by yeshey on 2019-09-11
Oh. That explains it.
So it's basically because of the ability to enlarge an LVM-ext4 Logical Volume whilst it's mounted that people use LVM.
Odd that I didn't stumble upon that information while doing my research, seems like such a crucial thing.
I'll keep that information in the back of my head until I'm able to use it or share it somewhere so that this moment... Was at least a little bit worthwhile for you :)

Cheers

---

