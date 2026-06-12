---
title: "Checking drives for errors"
date: 2013-06-20
forum: General Help
---

### Post by makamba on 2013-06-20
Hi,

I might have a really sick puppy as dual boot system. Recently I found out I had bad sectors on my hard drive. From an occasional 'Checking drives for errors' while booting it went to each time I booted Ubuntu. I checked my partitions using badblocks (I believe). That check resulted in me knowing of the bad sectors in my home drive. I checked some other partitions I use under Ubuntu, and these checks resulted in (0/0/0) errors. 

I decided to create space on Windows partitions, and move my /home to these (merged) partitions. However, since completion I have booted several times, and still the 'Checking drives for errors' message persists. 

When I cancel it I also have an occasional message that crytswap1 was not ready when Ubuntu tried to mount it. Is this the culprit? It does not have to be an encrypted swap file, my file system is not encrypted. 

My entry in the fstab is:
```

# swap was on /dev/sda9 during installation
#UUID=38232412-528d-41a4-82c8-8e6d65eaaaf none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```

Should I remove the hash before the UUID, and move it before the line containing the cryptswap1?

TIA,
Makamba

---

### Post by Bashing-om on 2013-06-20
makamba; Hi !

Yes, having cryptswap1 (un)intentional can cause problems... I am willing to work with you to correct the issue,
Show what we are working with-> post the output of terminal codes:
```

sudo blkid
sudo fdisk -lu
sudo dmsetup status
ls -la /dev/mapper/cryptswap1 ##just to see if this file exist.

```
Then we can redo the swap partition.
Be aware, limit writing to that disk as little as possible so as not to hinder "recovery" operations. Do only what has to be done until the overall health of the disk has been assertained. Bad sectors on the hard disk, in the event that the onboard error correcting routines can not reallocate additional sectors, you are indeed in deep trouble; Back up your data and continue to use that disk at your own risk, to a loss of all data at any given time.[INDENT=2]I be try'n to help

[/INDENT]

---

### Post by makamba on 2013-06-21
Hi Bashing-om,

First off, thanks for your reply. The requested information:
```
me@home:~$ sudo blkid
/dev/sda1: LABEL="Harde schijf" UUID="3A58E18258E13CEF" TYPE="ntfs" 
/dev/sda2: UUID="57825d60-616a-480e-bae7-4e044ac31183" TYPE="ext3" 
/dev/sda5: LABEL="Development" UUID="CCA00FA4A00F945C" TYPE="ntfs" 
/dev/sda6: LABEL="Muziek" UUID="B00C31B10C317386" TYPE="ntfs" 
/dev/sda7: LABEL="Niet meer vrij" UUID="DE4817804817571D" TYPE="ntfs" 
/dev/sda8: UUID="e6813a59-b8ec-4f6f-9b61-7651d77f459f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda9: LABEL="Comics" UUID="845CE6995CE684F0" TYPE="ntfs" 
/dev/sda10: UUID="848d600a-f793-485b-816d-0d75a76c1f5c" TYPE="ext4" 
/dev/sda12: LABEL="NewHome" UUID="83e6cd6c-8591-43b8-987d-e2ca229ec576" TYPE="ext3" 
/dev/sdb1: UUID="56e96ed1-4787-4081-afbc-3f4e77f6b2d2" TYPE="ext3" 
```
No sda11?

```
me@home:~$ sudo fdisk -lu
Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x64bdceff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   102414374    51207156    7  HPFS/NTFS/exFAT
/dev/sda2       102414375   409609304   153597465   83  Linux
/dev/sda3       409609366  1465144064   527767349+   5  Extended
/dev/sda5       409609368   512007614    51199123+   7  HPFS/NTFS/exFAT
/dev/sda6       512007678   614405924    51199123+   7  HPFS/NTFS/exFAT
/dev/sda7       614405988   716804234    51199123+   7  HPFS/NTFS/exFAT
/dev/sda8       741978153   916990199    87506023+  83  Linux
/dev/sda9      1331194158  1465144064    66974953+   7  HPFS/NTFS/exFAT
/dev/sda10      716806144   733853695     8523776   83  Linux
/dev/sda11      733855744   741978111     4061184   82  Linux swap / Solaris
/dev/sda12      916994048  1331193855   207099904   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bbe6c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   160071659    80035798+  83  Linux
```
Look, a sda11.

```
me@home:~$ sudo dmsetup status
No devices found
```
No logical device manager?

```
me@home:~$ ls -la /dev/mapper/cryptswap1
ls: cannot access /dev/mapper/cryptswap1: No such file or directory
```
If I can remember correctly, Ubuntu complained it had problems mounting cryptswap1. I did not see this message today. Did Ubunut give up trying to mount? Because it was not mounted.

---

### Post by Bashing-om on 2013-06-21
[COLOR=#000000]makamba; Hey ...

Does not look bad at all... appears all that needs doing is edit the swap entry in fstab, Maybe not even (re-)format the swap partition.

Let me see your complete "/etc/fstab" file to see how and what is mounted. 
```
cat /etc/fstab
```
The "dmsetup" command was just to make sure no encrypted partitions existed.
See;
```
man dmsetup
```[INDENT=3]
progress is made one step at a time

[/INDENT]
[INDENT=2]

[/INDENT]
 [/COLOR]

---

### Post by makamba on 2013-06-22
This is my fstab:
```

# / (root) was on /dev/sda13 during installation
UUID=848d600a-f793-485b-816d-0d75a76c1f5c /               ext4    errors=remount-ro 0       1

# Nieuwe home partitie
UUID=83e6cd6c-8591-43b8-987d-e2ca229ec576 /home     ext3    nodev,nosuid  0   2

# swap was on /dev/sda9 during installation
#UUID=38232412-528d-41a4-82c8-8e6d65e7e46f none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

# Music disk
UUID=B00C31B10C317386 /home/me/Muziek    ntfs    nls=iso8859-1,ro,umask=0 0 0

# Second harddrive
UUID=56e96ed1-4787-4081-afbc-3f4e77f6b2d2 /home/me/Downloads/Stuff2    ext3    defaults        0       2

# Previously lost partition
UUID=57825d60-616a-480e-bae7-4e044ac31183 /home/me/Downloads/Stuff3    ext3    defaults,user,exec,dev,suid        0       2

# ================ </^\> ================
# (OLD) /home was on /dev/sda8 during installation
# UUID=e6813a59-b8ec-4f6f-9b61-7651d77f459f /home           ext3    defaults        0       2

```

I had troubles with my old home drive, bad sectors and such. That's why it is commented out here. In the future I plan to format the disk, and mark the bad sectors as bad.

---

### Post by 3rdalbum on 2013-06-22
Your hard disk has already marked the sectors as bad, and will reallocate them to the disk's spare sectors that have been kept in reserve.

If you have a large number of bad sectors (more than the number of spare sectors), you need to throw away the disk otherwise you will get more and more bad sectors, and continue to lose data.

---

### Post by Bashing-om on 2013-06-22
[COLOR=#000000]makamba; Hey..

Presently you have no swap partition on the disk(s)- per "blkid"-  and therefore no definition of such in "/etc/fstab". It is highly recommended to use a swap partition, though if you do have a large amount of ram, a smaller swap partition (or maybe a swap file) may be used. -sda11 ??

That said, we are not going to write anything to that disk until your data is "saved" and the overall health of the disk is determined.
Comment out this needless line in "/etc/fstab" 
[/COLOR]> [COLOR=#000000][FONT=Ubuntu Mono]/dev/mapper/cryptswap1 none swap sw 0 0[/FONT][/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]reboot
and run the S.M.A.R.T. diagnostics (disk utility) -> with the system at idle;
Depending on the latest results from this testing,  depends on what we do next. -worst case- ,You are looking at wiping that drive out completely and reformatting it ... perhaps can be of some salvage and use... Testing and time will tell.

Will take a look at sda11... see what the haps with it is at that time.
[/COLOR][INDENT=2][COLOR=#000000]
no harm in try'n

[/COLOR][/INDENT]

---

### Post by makamba on 2013-06-23
As requested, I commented out the line with cryptswap1.

Looking at the output of the 'Disk utility' I (still?) get 26 sectors  with the 'Reallocated Sector Count' and 528 sectors with the 'Current  Pending Sector Count'. 

I moved data from my old /home to a new partition, currently my new  /home. That partition checks out fine. The root partition checked with  'badblocks' checks out fine too.

```
macamba@Hermod:~$ sudo badblocks -sv /dev/sda12
me@home:~$ sudo badblocks -sv /dev/sda12
Checking blocks 0 to 207099903
Checking for bad blocks (read-only test):   0.00% done, 0:00 elapsed.  (0/0/0 errdone                                                 
Pass completed, 0 bad blocks found. (0/0/0 errors)

me@home:~/Downloads/Stuff2$ sudo badblocks -sv /dev/sda13
Checking blocks 0 to 8523775
Checking for bad blocks (read-only test):   0.00% done, 0:00 elapsed.  (0/0/0 errdone                                                 
Pass completed, 0 bad blocks found. (0/0/0 errors)

```

Would it help to delete /dev/sda8 (my old /home drive) in gparted or the Disk Utility? Or should I subsequently format it to ext3 too?

---

### Post by Bashing-om on 2013-06-23
makamba; Hey,

One step at a time, let us get that system stable and functioning:
```
sudo blkid -c /dev/null -o list  ## To clear cache and get new view:
ls -l /dev/disk/by-uuid/38232412-528d-41a4-82c8-8e6d65eaaaf
ls /dev/disk/by-uuid -alh
sudo blkid /dev/sda11 -c /dev/null

```
Now IF:
sda11 exist and
the uuid of sda11 == 38232412-528d-41a4-82c8-8e6d65eaaaf in all respects and all agree;
Just to make sure we do not have to (re)create the swap partition !
Then; make a backup of the current /etc/fstab and insert these lines in place of those present:
```

# swap is on /dev/sda11 for this installation: 
UUID=38232412-528d-41a4-82c8-8e6d65eaaaf none            swap    sw              0       0

```
To try your new configuration immediately and insure there are no errors, you have to reload /etc/fstab:
```

sudo mount -a

```
If no errors then reboot the system;
A new look at things:
```

sudo fdisk -lu
sudo blkid

```

Then we will discuss what to do !

---

### Post by makamba on 2013-06-23
And if something went wrong after the 'sudo mount -a' I should restore the old fstab?

---

### Post by Bashing-om on 2013-06-23
[COLOR=#000000]makamba; Hey;

There is nothing that "should" go wrong, but if so (typo for instance); then:
find the error in the current fstab file prior to rebooting; -> "mount -a" to retest;
else, yes one may copy back the "messed up" fstab file and be back whence you started.
[/COLOR][INDENT][COLOR=#000000]
caution is commendable

[/COLOR][/INDENT]

---

### Post by makamba on 2013-06-24
> **Bashing-om said:**
> 
```
sudo blkid -c /dev/null -o list ) ## To clear cache and get new view:
ls -l /dev/disk/by-uuid/38232412-528d-41a4-82c8-8e6d65eaaaf

```

That went wrong. I got a 
```
me@home:~$ ls -l /dev/disk/by-uuid/38232412-528d-41a4-82c8-8e6d65eaaaf
ls: cannot access /dev/disk/by-uuid/38232412-528d-41a4-82c8-8e6d65eaaaf: No such file or directory

```

```

ls /dev/disk/by-uuid -alh
lrwxrwxrwx 1 root root  10 Jun 24 08:02 3A58E18258E13CEF -> ../../sda1
lrwxrwxrwx 1 root root  10 Jun 24 08:11 56e96ed1-4787-4081-afbc-3f4e77f6b2d2 -> ../../sdb1
lrwxrwxrwx 1 root root  10 Jun 24 08:12 57825d60-616a-480e-bae7-4e044ac31183 -> ../../sda2
lrwxrwxrwx 1 root root  11 Jun 24 08:08 83e6cd6c-8591-43b8-987d-e2ca229ec576 -> ../../sda12
lrwxrwxrwx 1 root root  10 Jun 24 08:02 845CE6995CE684F0 -> ../../sda9
lrwxrwxrwx 1 root root  11 Jun 24 08:03 848d600a-f793-485b-816d-0d75a76c1f5c -> ../../sda10
lrwxrwxrwx 1 root root  10 Jun 24 08:02 B00C31B10C317386 -> ../../sda6
lrwxrwxrwx 1 root root  10 Jun 24 08:02 CCA00FA4A00F945C -> ../../sda5
lrwxrwxrwx 1 root root  10 Jun 24 08:02 DE4817804817571D -> ../../sda7
lrwxrwxrwx 1 root root  10 Jun 24 08:02 e6813a59-b8ec-4f6f-9b61-7651d77f459f -> ../../sda8

```
Nope, no sda11. The fairies took it. 

```

sudo blkid /dev/sda11 -c /dev/null
me@home:~ $

```
So, no output. And it insist to being there when I perform a 'sudo fdisk -lu'.

> **Bashing-om said:**
> Now IF:
sda11 exist and
the uuid of sda11 == 38232412-528d-41a4-82c8-8e6d65eaaaf in all respects and all agree;
Just to make sure we do not have to (re)create the swap partition !


So, am I correct in assuming we have to recreate the swap partition? It did not come to the front in the previous instructions (with the exception of the 'sudo fdisk -lu'). Do I need to create a new swap partition, as explained in [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)?

TIA,
Macamba

---

### Post by Bashing-om on 2013-06-24
makamba; Hey,
Sort of taken aback... but, no big deal ...let us just wipe out any existence of "cryptswap1" - if  any - and redo the swap partition.

And yeah your link is a good one... pleased you are doing your homework.
Terminal codes:
```

sudo swapoff -a
sudo cryptsetup remove /dev/mapper/cryptswap1 ## probably does not exist.
ls -ld /etc/crypttab ## probably does not exist, but if so then do the next commands.
gksudo gedit /etc/crypttab
*remove the /dev/sda11 line*
sudo /sbin/mkswap /dev/sda11
sudo swapon /dev/sda11
sudo blkid -c /dev/null -o list ##to get the new UUID for sda11.
gksudo gedit /etc/fstab ##replace the uuid with the new UUID in the "swap" line.
##save and exit back to terminal.
sudo mount -a ##no output is a good thing

```

I really did not want to write to that disk until your data was backed up and safe, and the health status of the disk was insured, more on that later. Most important is to get the system stable with what it has to work with !

This will cover all the bases and give confidence in having a stable system to work from, for the forthcoming operations.
[INDENT=2]
it is but a process

[/INDENT]

---

### Post by makamba on 2013-06-25
Bashing-om; Hey ;)
Thanks for the help so far 

> **Bashing-om said:**
> makamba; Hey,
Sort of taken aback... but, no big deal ...let us just wipe out any existence of "cryptswap1" - if  any - and redo the swap partition.

And yeah your link is a good one... pleased you are doing your homework.
Terminal codes:
```

sudo swapoff -a
sudo cryptsetup remove /dev/mapper/cryptswap1 ## probably does not exist.
ls -ld /etc/crypttab ## probably does not exist, but if so then do the next commands.
gksudo gedit /etc/crypttab
*remove the /dev/sda11 line*   # I commented it out
sudo /sbin/mkswap /dev/sda11
sudo swapon /dev/sda11

```

Pity:
```

me@home:~$ sudo swapon /dev/sda11
swapon: /dev/sda11: read swap header failed: Invalid argument

```
Did that break it? Is it a "known" bug? [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/569031](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/569031)

I just remembered that the configuration (of partitions in Windows and Linux) I have is in use for some time. I had an older version of Linux running. But after the message that my version would not be supported anymore I changed to the newest LTS version available. Might that something to be considered?

```

me@home:~$ sudo blkid -c /dev/null
/dev/sda1: LABEL="Harde schijf" UUID="3A58E18258E13CEF" TYPE="ntfs" 
/dev/sda2: UUID="57825d60-616a-480e-bae7-4e044ac31183" TYPE="ext3" 
/dev/sda5: LABEL="Development" UUID="CCA00FA4A00F945C" TYPE="ntfs" 
/dev/sda6: LABEL="Muziek" UUID="B00C31B10C317386" TYPE="ntfs" 
/dev/sda7: LABEL="Niet meer vrij" UUID="DE4817804817571D" TYPE="ntfs" 
/dev/sda8: UUID="e6813a59-b8ec-4f6f-9b61-7651d77f459f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda9: LABEL="Comics" UUID="845CE6995CE684F0" TYPE="ntfs" 
/dev/sda10: UUID="848d600a-f793-485b-816d-0d75a76c1f5c" TYPE="ext4" 
/dev/sda12: LABEL="NewHome" UUID="83e6cd6c-8591-43b8-987d-e2ca229ec576" TYPE="ext3" 
/dev/sdb1: UUID="56e96ed1-4787-4081-afbc-3f4e77f6b2d2" TYPE="ext3" 

```

No sda11? I think I can stop with continuing your instructions. And as far as I can see I did not change anything major I can keep it as it is (Famous last words? My cryptswap was not used anyway).

And I looked back in this post and saw that I did not check for badblocks on sda11. So:```

me@home:~$ sudo badblocks -sv /dev/sda11
Checking blocks 0 to 4061183
Checking for bad blocks (read-only test):   0.00% done, 0:00 elapsed. (0/0/0 errdone                                                 
Pass completed, 0 bad blocks found. (0/0/0 errors)

```
... none.

---

### Post by makamba on 2013-06-25
And then I saw that a swapon -va worked as it should be, by not giving back any feedback. So I continued your instructions without a hitch, and in the end rebooted. As I had no problems while booting (my system did not check for errors on the disks either) I think my problems are solved. Thanks for the help.

---

### Post by Bashing-om on 2013-06-25
[COLOR=#000000]makamba;

Outstanding... pleased you got it resolved... was starting to wonder how deep we were going to have to go...and what would drive the system that we had to go deeper...
[/COLOR][INDENT=3][COLOR=#000000]
keep on keep'n on

[/COLOR][/INDENT]

---

