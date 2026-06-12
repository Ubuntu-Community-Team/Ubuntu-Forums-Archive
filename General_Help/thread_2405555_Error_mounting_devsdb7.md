---
title: "Error mounting /dev/sdb7"
date: 2018-11-07
forum: General Help
---

### Post by MibunoOokami on 2018-11-07
Hello everyone, sorry for the long post,

I got a call last night from a distressed friend who did a window$ update and can't access Ubuntu anymore. Having put their mind at ease letting them know it'll be as simple as making a backup and then updating grub, I brought the machine to my place to begin the work.  I have included output from some troubleshooting tips on another (solved) thread with a similar problem. The aforementioned thread is a little difficult for me to follow as the issue looks somewhat different. It indicates filesystem check/repair is required, there's only so many things I'm happy to try without being able to back up the machine. 

Upon booting up with a live CD and attempting to first open the partition that needs backing up, I have been greeted with the following error, which I have never seen before. I've tried troubleshooting this myself and am not having much luck. I really would appreciate any 

```
Error mounting /dev/sdb7 at /media/ubuntu/64de21bd-d4ab-467e-91ea-e3695662b11f: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb7" "/media/ubuntu/64de21bd-d4ab-467e-91ea-e3695662b11f"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb7, 
       missing codepage or helper program, or other error 
       In some cases useful info is found in syslog - try 
       dmesg | tail  or so
```

The output of  dmesg | tail doesn't mean anything to me. I don't want to have to eat my words and say getting the grub menu back isn't as simple as I said, so I would really appreciate your help in finding out what is going on and how to resolve this problem. Thanks in advance.

```
ubuntu@ubuntu:~$ dmesg | tail 
[  338.800164] end_request: I/O error, dev sr0, sector 859944 
[  356.188410] JBD2: Unrecognised features on journal 
[  356.188417] EXT4-fs (sdb7): error loading journal 
[  504.625872] wlan0: authenticate with a4:91:b1:44:4b:8d 
[  504.646266] wlan0: send auth to a4:91:b1:44:4b:8d (try 1/3) 
[  504.648222] wlan0: authenticated 
[  504.653088] wlan0: associate with a4:91:b1:44:4b:8d (try 1/3) 
[  504.657194] wlan0: RX AssocResp from a4:91:b1:44:4b:8d (capab=0x1411 status=0 aid=1) 
[  504.657261] wlan0: associated 
[  504.657306] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
```

```
ubuntu@ubuntu:~$ sudo parted -l 
Model: ATA WDC WD10JPVX-22J (scsi) 
Disk /dev/sdb: 1000GB 
Sector size (logical/physical): 512B/4096B 
Partition Table: gpt 
 
Number  Start   End     Size    File system  Name                          Flags 
 1      1049kB  524MB   523MB   ntfs         Basic data partition          hidden, diag 
 2      524MB   629MB   105MB   fat32        EFI system partition          boot 
 3      629MB   646MB   16.8MB               Microsoft reserved partition  msftres 
 4      646MB   53.3GB  52.7GB  ntfs         Basic data partition          msftdata 
 5      53.3GB  53.9GB  512MB   fat32                                      boot 
 6      53.9GB  85.5GB  31.6GB  ext4 
 7      85.5GB  1000GB  915GB   ext4 
 
 
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 
has been opened read-only. 
Error: Can't have a partition outside the disk!  
```

```
ubuntu@ubuntu:~$ cat /etc/fstab 
overlayfs / overlayfs rw 0 0 
tmpfs /tmp tmpfs nosuid,nodev 0 0 
```

Again, I would really appreciate your help with this. Thank you in advance.

---

### Post by HermanAB on 2018-11-08
It looks to me as if one of the ext4 disk partitions /dev/sr0 is corrupted.

---

### Post by MibunoOokami on 2018-11-08
> **HermanAB said:**
> It looks to me as if one of the ext4 disk partitions /dev/sr0 is corrupted.

Isn't that the optical drive? I'm using a physical CD rather than USB because I seem to recall issues getting it to recognise a USB. The CD itself shouldn't be corrupt as I have used it for installing Ubuntu in the past, so could it be the optical drive is failing and causing this problem?

---

### Post by westie457 on 2018-11-08
Maybe the info here might be of some help. [https://ubuntuforums.org/showthread.php?t=2253608&p=13171637#post13171637](https://ubuntuforums.org/showthread.php?t=2253608&p=13171637#post13171637)

---

### Post by MibunoOokami on 2018-11-08
> **westie457 said:**
> Maybe the info here might be of some help. [https://ubuntuforums.org/showthread.php?t=2253608&p=13171637#post13171637](https://ubuntuforums.org/showthread.php?t=2253608&p=13171637#post13171637)

If I understand correctly, nothing (backup) can be done before doing a disk check? So there's potentially a risk of data being lost through this process?

Edit: Or is it I just don't need to use -y or -p, then I will be asked if want to fix if a problem is found, and can potentially say no? Although I guess that won't be very helpful to do.

Edit: Would the window$ update have been responsible for this?

---

### Post by MibunoOokami on 2018-11-08
After securing permission from the owner to go ahead and try resolve this without being able to do a backup, I ran the command ```
fdisk -l
``` and this is the output
```
ubuntu@ubuntu:~$ sudo fdisk -l 
 
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted. 
 
 
Disk /dev/sda: 8388 MB, 8388608000 bytes 
255 heads, 63 sectors/track, 1019 cylinders, total 16384000 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x663eb4c4 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           0     3815135     1907568    0  Empty 
/dev/sda2         3737268     3741939        2336   ef  EFI (FAT-12/16/32) 
 
WARNING: GPT (GUID Partition Table) detected on '/dev/sda1'! The util fdisk doesn't support GPT. Use GNU Parted. 
 
 
Disk /dev/sda1: 1953 MB, 1953349632 bytes 
255 heads, 63 sectors/track, 237 cylinders, total 3815136 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x663eb4c4 
 
     Device Boot      Start         End      Blocks   Id  System 
/dev/sda1p1   *           0     3815135     1907568    0  Empty 
/dev/sda1p2         3737268     3741939        2336   ef  EFI (FAT-12/16/32) 
 
WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted. 
 
 
Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes 
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 4096 bytes 
I/O size (minimum/optimal): 4096 bytes / 4096 bytes 
Disk identifier: 0x45098b5c 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdc1               1  1953525167   976762583+  ee  GPT 
Partition 1 does not start on physical sector boundary. 
```

I don't know what to make of this, shouldn't I be seeing /dev/sdb in here?

---

### Post by MibunoOokami on 2018-11-08
> **MibunoOokami said:**
> 
I don't know what to make of this, shouldn't I be seeing /dev/sdb in here?

Okay, and the output of sudo e2fsck -C0 -p -f -v /dev/sdb7  

 ```
ubuntu@ubuntu:~$ 
 e2fsck: No such file or directory while trying to open /dev/sdb7 
 Possibly non-existent device? 
```
 

 and trying again with sudo e2fsck -C0 -p -f -v /dev/sdb
 

 ```
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sdb 
 e2fsck: No medium found while trying to open /dev/sdb 
 /dev/sdb:  
 The superblock could not be read or does not describe a valid ext2/ext3/ext4 
 filesystem.  If the device is valid and it really contains an ext2/ext3/ext4 
 filesystem (and not swap or ufs or something else), then the superblock 
 is corrupt, and you might try running e2fsck with an alternate superblock: 
     e2fsck -b 8193 <device> 
  or 
     e2fsck -b 32768 <device> 
```

Am I right in thinking this is a very serious problem with my friend's machine? Is it fixable?

---

### Post by MibunoOokami on 2018-11-08
FWIW, evidently for the past six months or so Ubuntu had been freezing every other day, so my friend would have to do a forced reboot/shutdown to resolve that issue. I'm told the computer was being used throughout the day, but this problem of freezing happened predominantly at night.

---

### Post by Bashing-om on 2018-11-09
MibunoOokami; Ouch !

This could be a real tough nut to crack.

What drives are seen in bios when booting ?
If all drives are seen hardware wise we can then start at the bottom and see what we can work out,
What operating system and on which drive are you booting ?

Else:
Do you have a liveUSB onhand ?

[INDENT][INDENT]see what might be done
[/INDENT][/INDENT]

---

### Post by MibunoOokami on 2018-11-09
> **Bashing-om said:**
> MibunoOokami; Ouch !

This could be a real tough nut to crack.

What drives are seen in bios when booting ?
If all drives are seen hardware wise we can then start at the bottom and see what we can work out,
What operating system and on which drive are you booting ?

Else:
Do you have a liveUSB onhand ?[INDENT][INDENT]see what might be done
[/INDENT]
[/INDENT]


Ooh I got bad news about BIOS... It's PW protected and the owner doesn't know what it is, so don't know what drives are seen. I have a live USB good to go, but need access to BIOS. Not sure how much difference there is, but I am able to use a LiveCD instead with no issues.

The OS I believe to be Windows 7 or 10, couldn't tell you which drive is booting.

EDIT: So it's probably a good thing i didn't dive straight in and play with Testdisk?

---

### Post by Bashing-om on 2018-11-09
MibunoOokami; Well ...

Going off half-cocked one is sure to shoot oneself in the foot.
If the hardware does not see the drive, no software will either.

When I boot, all my drives are indicated on the bios splash screen, this is not similar ? 

[INDENT][INDENT]what a way to do things
[/INDENT][/INDENT]

---

### Post by MibunoOokami on 2018-11-09
I can't say I've ever noticed that. I will check now.

---

### Post by MibunoOokami on 2018-11-10
Nope, I can't see the drives being listed. But as I went to check that out, window$ decided it wanted to try an auto disk repair, but stopped.

---

### Post by Bashing-om on 2018-11-10
MibunoOokami; Hummm ...

Boot the liveCD.
What shows for
```

sudo parted -l

```

[INDENT]poke'n to see if anything is revealed
[/INDENT]

---

### Post by MibunoOokami on 2018-11-10
> **Bashing-om said:**
> MibunoOokami; Hummm ...

Boot the liveCD.
What shows for
```

sudo parted -l

```
[INDENT]poke'n to see if anything is revealed
[/INDENT]


When I started this thread a couple of days ago the output was ```

ubuntu@ubuntu:~$ sudo parted -l 
Model: ATA WDC WD10JPVX-22J (scsi) 
Disk /dev/sdb: 1000GB 
Sector size (logical/physical): 512B/4096B 
Partition Table: gpt 
 
Number  Start   End     Size    File system  Name                          Flags 
 1      1049kB  524MB   523MB   ntfs         Basic data partition          hidden, diag 
 2      524MB   629MB   105MB   fat32        EFI system partition          boot 
 3      629MB   646MB   16.8MB               Microsoft reserved partition  msftres 
 4      646MB   53.3GB  52.7GB  ntfs         Basic data partition          msftdata 
 5      53.3GB  53.9GB  512MB   fat32                                      boot 
 6      53.9GB  85.5GB  31.6GB  ext4 
 7      85.5GB  1000GB  915GB   ext4 
 
 
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 
has been opened read-only. 
Error: Can't have a partition outside the disk!
```

Just now however, just now ```
ubuntu@ubuntu:~$ sudo parted -l
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No? ^C                                                                
Error: Both the primary and backup GPT tables are corrupt.  Try making a fresh
table, and using Parted's rescue feature to recover partitions.

Model: ATA WDC WD10JPVX-22J (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  524MB   523MB   ntfs         Basic data partition          hidden, diag
 2      524MB   629MB   105MB   fat32        EFI system partition          boot
 3      629MB   646MB   16.8MB               Microsoft reserved partition  msftres
 4      646MB   53.3GB  52.7GB  ntfs         Basic data partition          msftdata
 5      53.3GB  53.9GB  512MB   fat32                                      boot
 6      53.9GB  85.5GB  31.6GB  ext4
 7      85.5GB  1000GB  915GB   ext4


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!
```

Note, I accidentally pressed Ctrl+C to try and copy the first part before clicking Y/N and it used that as an answer.

---

### Post by Bashing-om on 2018-11-10
MibunoOokami; Well -

does not look good for the home team.

what shows:
```

ls -l /dev/disk/by-uuid/

```

[INDENT]which way did he go, George[/INDENT]

---

### Post by MibunoOokami on 2018-11-10
```
ubuntu@ubuntu:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 Nov 10 05:02 64de21bd-d4ab-467e-91ea-e3695662b11f -> ../../sdc7
lrwxrwxrwx 1 root root 10 Nov 10 05:02 7a21c3df-8067-4661-953a-7d7404c3e2d1 -> ../../sdc6
lrwxrwxrwx 1 root root 10 Nov 10 05:02 7CE85440E853F6BC -> ../../sdc1
lrwxrwxrwx 1 root root 10 Nov 10 05:02 ABC1-C43A -> ../../sdc5
lrwxrwxrwx 1 root root 10 Nov 10 05:02 AE55-7A3F -> ../../sdc2
lrwxrwxrwx 1 root root 10 Nov 10 05:02 FA3657BC36577919 -> ../../sdc4


```

I think he went that way

---

### Post by Bashing-om on 2018-11-10
MibunoOokami; Well ..

Above my skill level at this point, With the 2 drives not seen I do not understand why the drive is identified as 'sdc' . I would expect it to be seen now as 'sda'.
We will have to see what those of the greater experience here can relate.

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by MibunoOokami on 2018-11-10
> **Bashing-om said:**
> MibunoOokami; Well ..

Above my skill level at this point, With the 2 drives not seen I do not understand why the drive is identified as 'sdc' . I would expect it to be seen now as 'sda'.
We will have to see what those of the greater experience here can relate.[INDENT][INDENT]sometimes I do wonder
[/INDENT]
[/INDENT]


Thanks for your assistance Bashing-om. Potentially is the HDD is poked?

---

### Post by Bashing-om on 2018-11-10
MibunoOokami;

were me at this point -- me - I would be swapping our drives between 2 computers to isolate it to hardware problems.

[INDENT]just do not know a better way
[/INDENT]

---

### Post by MibunoOokami on 2018-11-10
So if I put my HDD in this machine, and this machine's HDD in my machine, what exactly would that achieve? Is there potential my HDD could get messed up too if it's the machine causing problems?
Earlier I mentioned window$ tried to auto repair and stopped (because it wanted human intervention) do you think it worthwhile intervening and getting window$ to do a repair? I'm presuming it can see the drive/partitions.

---

### Post by 23dornot23d on 2018-11-10
on the first post there is this error

> 
Error: Can't have a partition outside the disk!


You would be as well dropping oldfred a personal message and asking if its the problem - then go from there ........

There are other posts showing what happens when this message comes up ....... but whether they apply to your own situation I cannot be sure

> 
window$ to do a repair? I'm presuming it can see the drive/partitions. 				


Never presume anything - especially when it can involve losing lots of data - but only your friend can decide how much useful data is on the drive.
there are ways of getting a lot of it off - or even making a copy/clone of the drive - before something happens that makes it non retrievable.

So oldfred is probably as good as anyone to look into this - if he is available. [https://ubuntuforums.org/member.php?u=852711](https://ubuntuforums.org/member.php?u=852711)

---

### Post by oldfred on 2018-11-10
If error is from sdb, post this in code tags:
sudo gdisk -l /dev/sdb

Do not use older live installer. Only newer versions of fdisk support gpt partitioned drives. You can use parted or gdisk, each gives slightly different and often useful info.

---

### Post by MibunoOokami on 2018-11-10
> **MibunoOokami said:**
> I can't say I've ever noticed that. I will check now.

> **MibunoOokami said:**
> Nope, I can't see the drives being listed.

Checked this on my own machine and per my earlier comments, still haven't seen the drives show on the splash screen.

> **23dornot23d said:**
> 
Never presume anything - especially when it can involve losing lots of data - but only your friend can decide how much useful data is on the drive.
there are ways of getting a lot of it off - or even making a copy/clone of the drive - before something happens that makes it non retrievable.

Ok, thanks for the heads up. I'm glad it's not my machine because I would have gone with my presumption and probably made a real mess of things.

> **oldfred said:**
> If error is from sdb, post this in code tags:
sudo gdisk -l /dev/sdb

Do not use older live installer. Only newer versions of fdisk support gpt partitioned drives. You can use parted or gdisk, each gives slightly different and often useful info.

Live installer being LiveCD? That could be a contributing factor, the latest version I have on disc is 14.04 I can't boot with USB because I need a PW for BIOS.

The output for now ```
ubuntu@ubuntu:~$ sudo gdisk -l /dev/sdb 
GPT fdisk (gdisk) version 0.8.8 
 
Partition table scan: 
  MBR: protective 
  BSD: not present 
  APM: not present 
  GPT: present 
 
Found valid GPT with protective MBR; using GPT. 
Disk /dev/sdb: 1953525168 sectors, 931.5 GiB 
Logical sector size: 512 bytes 
Disk identifier (GUID): 11B88084-F195-4744-8F41-594A07CD3829 
Partition table holds up to 128 entries 
First usable sector is 34, last usable sector is 1953525134 
Partitions will be aligned on 2048-sector boundaries 
Total free space is 4181 sectors (2.0 MiB) 
 
Number  Start (sector)    End (sector)  Size       Code  Name 
   1            2048         1023999   499.0 MiB   2700  Basic data partition 
   2         1024000         1228799   100.0 MiB   EF00  EFI system partition 
   3         1228800         1261567   16.0 MiB    0C01  Microsoft reserved part 
   4         1261568       104191255   49.1 GiB    0700  Basic data partition 
   5       104192000       105191423   488.0 MiB   EF00   
   6       105191424       166948863   29.4 GiB    8300   
   7       166948864      1953523711   851.9 GiB   8300  
```

---

### Post by MibunoOokami on 2018-11-10
I just went and got a blank DVD and put 18.04 on it. Here are the most up-to-date outputs of the various commands I have tried so far. There is some difference, I hope this will help.

```
ubuntu@ubuntu:~$ dmesg | tail
[ 1474.276606] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1490.151568] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1498.307229] wlp32s0: authenticate with a4:91:b1:44:4b:8d
[ 1498.320155] wlp32s0: send auth to a4:91:b1:44:4b:8d (try 1/3)
[ 1498.322124] wlp32s0: authenticated
[ 1498.324086] wlp32s0: associate with a4:91:b1:44:4b:8d (try 1/3)
[ 1498.328888] wlp32s0: RX AssocResp from a4:91:b1:44:4b:8d (capab=0x1411 status=0 aid=1)
[ 1498.329087] wlp32s0: associated
[ 1498.585427] IPv6: ADDRCONF(NETDEV_CHANGE): wlp32s0: link becomes ready
[ 1506.276620] Bluetooth: hci0: last event is not cmd complete (0x0f)
```

```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD10JPVX-22J (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  524MB   523MB   ntfs         Basic data partition          hidden, diag
 2      524MB   629MB   105MB   fat32        EFI system partition          boot, esp
 3      629MB   646MB   16.8MB               Microsoft reserved partition  msftres
 4      646MB   53.3GB  52.7GB  ntfs         Basic data partition          msftdata
 5      53.3GB  53.9GB  512MB   fat32                                      boot, esp
 6      53.9GB  85.5GB  31.6GB  ext4
 7      85.5GB  1000GB  915GB   ext4


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Model: HL-DT-ST DVDRAM GUE1N (scsi)                                       
Disk /dev/sr0: 1953MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac
Disk Flags: 

Number  Start   End     Size    File system  Name   Flags
 1      2048B   6143B   4096B                Apple
 2      1913MB  1916MB  2392kB               EFI
```

```
ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/loop0: 1.8 GiB, 1864450048 bytes, 3641504 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 86.9 MiB, 91099136 bytes, 177928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 34.7 MiB, 36323328 bytes, 70944 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 140.9 MiB, 147722240 bytes, 288520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 2.3 MiB, 2433024 bytes, 4752 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 14.5 MiB, 15196160 bytes, 29680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 3.7 MiB, 3887104 bytes, 7592 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 11B88084-F195-4744-8F41-594A07CD3829

Device         Start        End    Sectors   Size Type
/dev/sda1       2048    1023999    1021952   499M Windows recovery environment
/dev/sda2    1024000    1228799     204800   100M EFI System
/dev/sda3    1228800    1261567      32768    16M Microsoft reserved
/dev/sda4    1261568  104191255  102929688  49.1G Microsoft basic data
/dev/sda5  104192000  105191423     999424   488M EFI System
/dev/sda6  105191424  166948863   61757440  29.5G Linux filesystem
/dev/sda7  166948864 1953523711 1786574848 851.9G Linux filesystem
```

That (above) looks completely different now, and I notice the partitions are now sda1-7

```
ubuntu@ubuntu:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root  9 Nov 10 18:17 2018-07-25-03-21-56-00 -> ../../sr0
lrwxrwxrwx 1 root root 10 Nov 10 18:44 64de21bd-d4ab-467e-91ea-e3695662b11f -> ../../sda7
lrwxrwxrwx 1 root root 10 Nov 10 18:44 7CE85440E853F6BC -> ../../sda1
lrwxrwxrwx 1 root root 10 Nov 10 18:44 7a21c3df-8067-4661-953a-7d7404c3e2d1 -> ../../sda6
lrwxrwxrwx 1 root root 10 Nov 10 18:44 ABC1-C43A -> ../../sda5
lrwxrwxrwx 1 root root 10 Nov 10 18:44 AE55-7A3F -> ../../sda2
lrwxrwxrwx 1 root root 10 Nov 10 18:44 FA3657BC36577919 -> ../../sda4
```

```
ubuntu@ubuntu:~$ sudo gdisk -l /dev/sdb
GPT fdisk (gdisk) version 1.0.3

Problem opening /dev/sdb for reading! Error is 123.
```

---

### Post by oldfred on 2018-11-10
See this, post #2 by author of gdisk:
[https://ubuntuforums.org/showthread.php?t=1490819](https://ubuntuforums.org/showthread.php?t=1490819)

It is saying drive may have issues. Double check that all cables are tightly connected.
Then in Disks, upper right corner is Smart Status. It will say good or bad, and can run many tests. Do not know details on tests.

---

### Post by MibunoOokami on 2018-11-10
> **oldfred said:**
> See this, post #2 by author of gdisk:
[https://ubuntuforums.org/showthread.php?t=1490819](https://ubuntuforums.org/showthread.php?t=1490819)

It is saying drive may have issues. Double check that all cables are tightly connected.
Then in Disks, upper right corner is Smart Status. It will say good or bad, and can run many tests. Do not know details on tests.

I've got the back off the machine and found a lot of play in the optical drive and the HDD. The HDD screws all got about 3/4 - 1 turn to tighten them, cables seem secure.

Two questions before I put the cover back on and try the smart status:

 #1 I've tightened the optical drive screw as far as it will go, possibly over done it, yet the drive still moves a good 1-2mm is that normal? It looks like I may be able to fold a bit of pater, or perhaps put some aluminium tape in there there to reduce the play, would you recommend that if the play is not normal?

#2 Whilst I have the back off, would now be a good time to try and reset the BIOS PW? Or should that be a later task once we've established what's going on?

Thanks

---

### Post by oldfred on 2018-11-10
If you have case open, you might as well reset BIOS. You may jumper pins or remove motherboard battery for a bit.
Also then a good idea to see if a newer version of UEFI/BIOS is available from vendor & update it.

---

### Post by MibunoOokami on 2018-11-10
After 2.5 - 3hrs waiting for the extensive Smart disk check to complete, the results are "last self-test completed successfully" and the "disk is OK"
I still get the same output error ```
ubuntu@ubuntu:~$ sudo gdisk -l /dev/sdb
GPT fdisk (gdisk) version 1.0.3

Problem opening /dev/sdb for reading! Error is 123.
```

---

### Post by MibunoOokami on 2018-11-11
> **oldfred said:**
> See this, post #2 by author of gdisk:
[https://ubuntuforums.org/showthread.php?t=1490819](https://ubuntuforums.org/showthread.php?t=1490819)

It is saying drive may have issues. Double check that all cables are tightly connected.
Then in Disks, upper right corner is Smart Status. It will say good or bad, and can run many tests. Do not know details on tests.

Per post #2 of that thread you linked, here is the output of dmesg | tail -n 20.
```
ubuntu@ubuntu:~$ dmesg | tail -n 20
[  505.263688] audit: type=1400 audit(1541917963.824:163): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.gnome-logs.gnome-logs" pid=3861 comm="apparmor_parser"
[  505.336116] audit: type=1400 audit(1541917963.900:164): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="/snap/core/4917/usr/lib/snapd/snap-confine" pid=3869 comm="apparmor_parser"
[  505.336120] audit: type=1400 audit(1541917963.900:165): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="/snap/core/4917/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=3869 comm="apparmor_parser"
[  505.340975] audit: type=1400 audit(1541917963.904:166): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap-update-ns.core" pid=3871 comm="apparmor_parser"
[  505.345355] audit: type=1400 audit(1541917963.908:167): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap.core.hook.configure" pid=3873 comm="apparmor_parser"
[  505.618027] audit: type=1400 audit(1541917964.180:168): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap-update-ns.gnome-logs" pid=3880 comm="apparmor_parser"
[  505.959040] audit: type=1400 audit(1541917964.520:169): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.gnome-logs.gnome-logs" pid=3882 comm="apparmor_parser"
[  506.500828] audit: type=1400 audit(1541917965.064:170): apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap-update-ns.gnome-system-monitor" pid=3982 comm="apparmor_parser"
[  506.589407] audit: type=1400 audit(1541917965.152:171): apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap.gnome-system-monitor.gnome-system-monitor" pid=3984 comm="apparmor_parser"
[  509.950544] kauditd_printk_skb: 46 callbacks suppressed
[  509.950546] audit: type=1400 audit(1541917968.968:218): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="/snap/core/4917/usr/lib/snapd/snap-confine" pid=4151 comm="apparmor_parser"
[  509.950550] audit: type=1400 audit(1541917968.968:219): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="/snap/core/4917/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=4151 comm="apparmor_parser"
[  509.954388] audit: type=1400 audit(1541917968.972:220): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap-update-ns.core" pid=4153 comm="apparmor_parser"
[  509.961531] audit: type=1400 audit(1541917968.980:221): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap.core.hook.configure" pid=4155 comm="apparmor_parser"
[  510.203762] audit: type=1400 audit(1541917969.220:222): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap-update-ns.gnome-system-monitor" pid=4162 comm="apparmor_parser"
[  510.516750] audit: type=1400 audit(1541917969.536:223): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.gnome-system-monitor.gnome-system-monitor" pid=4164 comm="apparmor_parser"
[  510.812986] audit: type=1400 audit(1541917969.832:224): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap-update-ns.gnome-system-monitor" pid=4171 comm="apparmor_parser"
[  511.135534] audit: type=1400 audit(1541917970.152:225): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="snap.gnome-system-monitor.gnome-system-monitor" pid=4173 comm="apparmor_parser"
[  511.208932] audit: type=1400 audit(1541917970.228:226): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="/snap/core/4917/usr/lib/snapd/snap-confine" pid=4180 comm="apparmor_parser"
[  511.208937] audit: type=1400 audit(1541917970.228:227): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="/snap/core/4917/usr/lib/snapd/snap-confine//mount-namespace-capture-helper" pid=4180 comm="apparmor_parser"


```
Any thoughts? Does this output produce any helpful info?

---

### Post by oldfred on 2018-11-11
The dmesg all looks like snap updates.

If using a DVD, this error is standard, or you ignore it.
			 				Error: Can't have a partition outside the disk! 			 		

Do you have two drives? 
My system will change my sda to sdb, if I plug in a flash drive.

Post this:
       sudo lshw -C Disk -short

---

### Post by MibunoOokami on 2018-11-11
> **oldfred said:**
> The dmesg all looks like snap updates.

If using a DVD, this error is standard, or you ignore it.
                             Error: Can't have a partition outside the disk!                      

Do you have two drives? 
My system will change my sda to sdb, if I plug in a flash drive.

Post this:
       sudo lshw -C Disk -short

Nope, just the one HDD. A few days ago I had a LiveUSB plugged in but I couldn’t boot with it due to BIOS settings, and removed it the day before yesterday I believe it was.

```
ubuntu@ubuntu:~$ sudo lshw -C Disk -short 
H/W path        Device      Class          Description
======================================================
/0/1/0.0.0      /dev/sda    disk           1TB WDC WD10JPVX-22J
/0/2/0.0.0      /dev/cdrom  disk           DVDRAM GUE1N
/0/2/0.0.0/0    /dev/cdrom  disk           
/0/3/0.0.0      /dev/sdb    disk           SD/MMC/MS PRO
/0/3/0.0.0/0    /dev/sdb    disk
```

---

### Post by MibunoOokami on 2018-11-11
> **MibunoOokami said:**
> Nope, just the one HDD. A few days ago I had a LiveUSB plugged in but I couldn’t boot with it due to BIOS settings, and removed it the day before yesterday I believe it was.

Oh, I am terribly sorry to you all for wasting your time. Upon reflecting on my last sentence, I decided to see if I can open that partition again… And it has worked. The USB must have been causing this problem, it never even clicked until just now. Since I can actually access that partition now, I will mark this thread as solved.
  
What a rookie mistake, and how embarrassing. :oops:

---

### Post by Bashing-om on 2018-11-11
MibunoOokami Well !!

LOL ...
'fdisk' was not lying - huh ? Can not see what is not :)
Pleased you came back and reported the root of the cause of the issue.

-it's all a process of learning-

---

