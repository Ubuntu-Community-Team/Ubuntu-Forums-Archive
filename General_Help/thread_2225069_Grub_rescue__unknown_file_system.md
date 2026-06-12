---
title: "Grub rescue / unknown file system"
date: 2014-05-19
forum: General Help
---

### Post by muemo on 2014-05-19
Hello!
I have a big problem, i cant boot my laptop any more. I always get a blackscreen with rescue grub>
(at present I am online with Linux Mint 15 Cinnamon Live CD, there everything works)
I have Linux Mint11, (yes, I know, this is much too old, but this is not the problem here...)

I guess, I crashed it like this:
This afternoon, I wanted to install something, and followed some instructions in wiki. I had to mount something, but i just typed in "mount -o" and nothing behind... (I had already entered sudo -i), and then i accidentally pressed the ENTER-Button.
After that, I stopped with Strg + C, and then closed the Terminal with exit.
Then I wanted to restart...

Further Information:
If I enter ```
rescue grub> ls [CODE]
in the beginning, i get: 
[CODE](hd0)  (hd0,msdos6)   (hd0,msdos5)   (hd0,msdos3)   (hd0,msdos2)   (hd0,msdos1)
```
If I then insert "ls X" (I tried all six brackets for X), I get
```
filesystem unknown
```

So far, so bad... I already googled around, looking for solutions, but couldnt find anything that might help (or I didnt dare to do it... )

Perhaps this might help you something:
One year ago, I postet the following thing (I was asking for some other things in a forum)
```
sudo fdisk -l
Platte /dev/sda: 500.1 GByte, 500107862016 Byte
255 Köpfe, 63 Sektoren/Spur, 60801 Zylinder[INDENT]Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xadf2723c

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1               1        1740    13972480   27  Unbekannt
/dev/sda2   *        1740        1753      102400    7  HPFS/NTFS
/dev/sda3            1753       34534   263317803    7  HPFS/NTFS
/dev/sda4           34535       60802   210991105    5  Erweiterte
/dev/sda5           34535       60298   206947328   83  Linux
/dev/sda6           60298       60802     4042752   82  Linux Swap / Solaris

Platte /dev/sdb: 500.1 GByte, 500107861504 Byte
255 Köpfe, 63 Sektoren/Spur, 60801 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa4b57300

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1               1       60801   488384000+   7  HPFS/NTFS[/INDENT]

```[INDENT]
[/INDENT]
I already postet this in the german forum 
[http://www.linuxmintusers.de/index.php?topic=19378.0](http://www.linuxmintusers.de/index.php?topic=19378.0), where I was asked to post what I get with sudo parted -l:

```
 sudo parted -l
Model: ATA SAMSUNG HM500JI (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  14.3GB  14.3GB  primary   ntfs            diag
 2      14.3GB  14.4GB  105MB   primary   ntfs            boot
 3      14.4GB  284GB   270GB   primary   ntfs
 4      284GB   500GB   216GB   extended
 5      284GB   496GB   212GB   logical
 6      496GB   500GB   4140MB  logical   linux-swap(v1)


Model: TOSHIBA MK8037GSX (scsi) 
```

now I installed Boot Info Script:
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    27,947,007    27,944,960  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     27,947,008    28,151,807       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          28,151,808   554,787,413   526,635,606   7 NTFS / exFAT / HPFS
/dev/sda4         554,788,862   976,771,071   421,982,210   5 Extended
/dev/sda5         554,788,864   968,683,519   413,894,656  83 Linux
/dev/sda6         968,685,568   976,771,071     8,085,504  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   156,280,319   156,280,257   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        CC962B8F962B78DA                       ntfs       Recovery
/dev/sda2        787CAF397CAEF0D4                       ntfs       System Reserved
/dev/sda3        366CB0E86CB0A451                       ntfs       
/dev/sda6        2b31593e-dcca-4769-8c27-87fc4fba20b9   swap       
/dev/sdb1        11F8-2E1B                              vfat       DataLux
/dev/sr0                                                iso9660    Linux Mint 15 Cinnamon 64-bit

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/mint/366CB0E86CB0A451 fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1        /media/mint/DataLux      vfat       (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
  No volume groups found
```
I hope somebody can help me!
Thank you very much!
muemo

---

### Post by oldfred on 2014-05-19
Boot script also cannot mount sda5, but partition table says it is Linux.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda5 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda5
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda5

Not sure I would try from a real old distribution, it may not even support ext4 if really old. Always have a current version live installer or repair CD for every system installed.

---

### Post by muemo on 2014-05-20
Hi! Thank you for your answer - but I m sorry, I dont understand what you mean... (perhaps because I m a noob or perhaps because I m German, i think both... )
The first line, I don t know what to do.
sudo e2fsc ... brings:
```
 sudo e2fsck -C0 -p -f -v /dev/sda5
e2fsck: Bad magic number in super-block while trying to open /dev/sda5
/dev/sda5: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

Can you recommend a very old distribution (what is "real old"?)

---

### Post by oldfred on 2014-05-20
I was suggestioning that you should use the latest or 14.04 for any repairs. That would have all the fixes and updates that old versions would not have and then may not work so well.

Was sda5 shown as Linux formatted, ext2, ext3 or ext4 formatted or some other Linux format? e2fsck is only for the ext family of formats and it is saying it cannot fix it.

Or try the alternative superblock as suggested in its error message. More info on that:

 [http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
Using alternative superblock to check ext3
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/)
List backup superblocks:
sudo dumpe2fs /dev/sda5 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda5
One user could not get partition unmounted (may have needed swapoff), but used another live distro

---

### Post by muemo on 2014-06-16
ok, thank you for commenting.
i could save all my data with R-Linux.
Then I installed the new ubuntu LTS :D.

---

