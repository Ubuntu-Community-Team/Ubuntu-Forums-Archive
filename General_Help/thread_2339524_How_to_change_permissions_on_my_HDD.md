---
title: "How to change permissions on my HDD?"
date: 2016-10-09
forum: General Help
---

### Post by javierdl on 2016-10-09
I want to be able to install games from Steam in 2nd drive (HDD). The main drive with Ubuntu is a SSD.
Problem is that only root is the owner at the moment.
[COLOR=#111111][FONT=Ubuntu]
Thanks guys,

JDL

[/FONT][/COLOR]

---

### Post by Bashing-om on 2016-10-09
javierdl; Hello;

Show us what you are working with:
Post back the outputs - between code tags - of terminal commands :
```

sudo parted -l
sudo fdisk-lu
sudo blkid -c /dev/null -o list
cat /etc/fstab

```
make sure you are not comparing apples and oranges . that this is OR is not ext4/NTFS file systems.
And that the (F)ile (S)ystem (TAB)le is consistent.

[INDENT][INDENT]it's all in the process
[/INDENT][/INDENT]

---

### Post by javierdl on 2016-10-09
Hi Bashing-om,

Thanks for asking:

```
sudo parted -l[sudo] password for javier: 
Model: ATA WDC WD10EZEX-21M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system     Name  Flags
 1      1049kB  538MB   537MB   fat32           EF    boot, esp
 5      538MB   301GB   300GB   ext4
 2      301GB   615GB   315GB   fat32                 msftdata
 3      615GB   992GB   377GB   fat32                 msftdata
 4      992GB   1000GB  8523MB  linux-swap(v1)        diag




Model: ATA Patriot Torch LE (scsi)
Disk /dev/sdb: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system     Name  Flags
 1      1049kB  211MB   210MB   fat32                 boot, esp
 2      211MB   228MB   16.8MB  ext4            Mi    msftres
 3      228MB   1026MB  799MB   ntfs                  msftdata
 4      1026MB  88.6GB  87.6GB  ntfs                  msftdata
 6      88.6GB  109GB   20.8GB  ext4
 7      109GB   110GB   386MB   linux-swap(v1)
 8      110GB   120GB   10.3GB  ext4




Model: TOSHIBA External USB 3.0 (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start  End     Size    Type     File system  Flags
 1      106MB  2000GB  2000GB  primary  ntfs




javier@javier-Predator-G3-710:/media/javier/ext4$ sudo fdisk -lu
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 1B1FA484-E02B-4FAA-906D-10D3D588B00B


Device          Start        End   Sectors   Size Type
/dev/sda1        2048    1050623   1048576   512M EFI System
/dev/sda2   586989568 1201389567 614400000   293G Microsoft basic data
/dev/sda3  1201389568 1936877567 735488000 350.7G Microsoft basic data
/dev/sda4  1936877568 1953523711  16646144     8G Windows recovery environment
/dev/sda5     1050624  586989567 585938944 279.4G Linux filesystem


Partition table entries are not in disk order.




Disk /dev/sdb: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: A62FCAC7-9491-47C0-BE48-46384F1AD03B


Device         Start       End   Sectors   Size Type
/dev/sdb1       2048    411647    409600   200M EFI System
/dev/sdb2     411648    444415     32768    16M Microsoft reserved
/dev/sdb3     444416   2004319   1559904 761.7M Microsoft basic data
/dev/sdb4    2004320 173001607 170997288  81.6G Microsoft basic data
/dev/sdb6  173002752 213577727  40574976  19.4G Linux filesystem
/dev/sdb7  213577728 214331391    753664   368M Linux swap
/dev/sdb8  214331392 234440703  20109312   9.6G Linux filesystem








Disk /dev/sdc: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x545e75e9


Device     Boot  Start        End    Sectors  Size Id Type
/dev/sdc1       206848 3907024064 3906817217  1.8T  7 HPFS/NTFS/exFAT
javier@javier-Predator-G3-710:/media/javier/ext4$ sudo blkid -c /dev/null -o list
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  vfat             (not mounted)  D45B-1044
/dev/sda2  vfat             (not mounted)  5968-2E1F
/dev/sda3  vfat             (not mounted)  5999-D4D5
/dev/sda4  swap             (not mounted)  e863d0f6-0ab2-4f1f-9fa3-55a652b02283
/dev/sda5  ext4    ext4     /media/javier/ext4 2bacbf62-7a77-4ab4-8b25-063e52381eaf
/dev/sdb1  vfat             /boot/efi      A023-0678
/dev/sdb2  ext4             (not mounted)  fb4b6aab-3aa9-4f22-ac08-957d3765f525
/dev/sdb3  ntfs             (not mounted)  01D21F5BB33EFBA0
/dev/sdb4  ntfs    Win10    (not mounted)  7B637EED5EAE730B
/dev/sdb6  ext4             /              649ff9fc-1a34-4427-9ca4-9310bff5963a
/dev/sdb7  swap             [SWAP]         db1e3a9e-cd9d-48de-8e42-e674b4fdb699
/dev/sdb8  ext4             /home          1c6d2b39-7de5-4e00-a7d4-7e237fb789f8
/dev/sdc1  ntfs    TOSHIBA  /media/javier/TOSHIBA A46CE4BB6CE488FE
javier@javier-Predator-G3-710:/media/javier/ext4$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=649ff9fc-1a34-4427-9ca4-9310bff5963a /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
#UUID=A023-0678  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/sda8 during installation
UUID=1c6d2b39-7de5-4e00-a7d4-7e237fb789f8 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=db1e3a9e-cd9d-48de-8e42-e674b4fdb699 none            swap    sw              0       0
UUID=A023-0678    /boot/efi    vfat    defaults    0    1



```

I guess I should have unmounted the ext HD (Toshiba) for this purpose.

---

### Post by Bashing-om on 2016-10-09
javierdl; OK;

We have a clearer picture now of what you are working with.
You are booting the 2nd hard drive - sdb - and 
on the 1st hard drive are several partitions.
On the 1st hard drive it is your desire to copy/install files to ONE of the partitions .

Now the question is, which partition on this 1st hard drive do you want to mount and access ? 
sda2 and sda3 are Windows fat32 file systems, and the access rights are set at the mount point
sda5 is a linux file system - ext4 - and the access right when auto-mounted is set in the /etc/fstab file.

One must exercise care with a fat32 file system as there is a 4 GB limit on file sizes !

Now again - upfront - might be a real trick here to " install games from Steam " on a separate hard drive from where the operating system is. I have not done it but I can accept one may have some hoops to jump through to make that happen .

still identifying the target
[INDENT][INDENT][INDENT]getting ready to shoot
[/INDENT][/INDENT][/INDENT]

---

### Post by javierdl on 2016-10-09
Thanks Bashing-om,
Right, totally forgot to mention where I'm trying to install: [B]sda5

[/B]Back to you...

---

### Post by Bashing-om on 2016-10-09
javierdl; Hokay ..

For a auto-mount I prefer to make the mount point in the /mnt directory . 
Now we are going to access the file system that is contained on sda5 . We need a mount point and a name .
What have you in mind for a good name ?
say maybe like 'steam-files' or such ..  your choice for the name for your thought/memory process .

What is presently listed in /mnt ?
show :
```

ls -al /mnt/

```
Perhaps you would like to use an existing mount point ?

How are your text editing skills ? ; as we will next add that mount point to the /etc/fstab file .

[INDENT][INDENT]pull the hammer back
[/INDENT][/INDENT]

---

### Post by javierdl on 2016-10-10
```
 ls -al /mnt/
total 8
drwxr-xr-x  2 root root 4096 Jul 19 16:42 .
drwxr-xr-x 25 root root 4096 Oct  9 20:42 ..



```

---

### Post by Bashing-om on 2016-10-10
javierdl; Welp;

We make up a mount point - ya like my suggestion ? the name can be what ever you choose. here I use "steam-files" .
Make the mount point in the primary operating system ( sdb):
Booted up in ubuntu from the sdb drive; Run:
```

sudo mkdir /mnt/steam-files

```
make sure this is what we want as the target:
```

sudo mount /dev/sda5 /mnt/steam-files
ls -al /mnt/steam-files

```
depending; maybe " sudo ls -al /mnt/steam-files " .
 and we like what we see and are now sure of the target to make sda5 automount at bootup of the sdb drive.

Making this arrangement : as we are done with checking, we UN-mount what we manually mounted.
```

sudo umount /dev/sda5

```

And finally now we make the mount in the file system table.
It is SOP to always make a backup of any file that one edits . always .. never can tell what might perchance - cheap insurance:
```

sudo cp /etc/fstab /etc/fstab-10Oct2016

```
and now we can fire up a favorite text editor - gedit as my reference for the editor :
```

sudo -H gedit /etc/fstab

```
which opens the file with the elevated privileges to edit a system file.
now add these 2 lines:
```

#mountpoint for sda5 steam-files added 10Oct2106
UUID=2bacbf62-7a77-4ab4-8b25-063e52381eaf /mnt/steam-files            ext4    defaults        0       2

```
All there is to it .. done here, save the file and close out the editor- back in terminal.

Now , have the system check the file for errors :
reload /etc/fstab:
```

sudo mount -a

```
No errors reported, then ->

finally we make "YOU" the owner of that partition AND ALL the files contained in that partition- per your request . now that may not make steam happy. Depending on your use case steam may want ownership ????
```

sudo chown -R javier:javier /mnt/steam-files

```

reboot the system !
See the results of your efforts:
booted from sdb:
```

ls -al /mnt/steam-files

```
verifies that YOU - javier - have access to that file system. /mnt/steam-files is your oyster to do with as YOU want.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by javierdl on 2016-10-11
I put the 2 lines of text at the bottom of the file. Was it there where I was to put them?

```
sudo -H gedit /etc/fstab

(gedit:29420): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files


** (gedit:29420): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-spell-enabled not supported


** (gedit:29420): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-encoding not supported


** (gedit:29420): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported



```

---

### Post by Bashing-om on 2016-10-11
javierdl; Hey .. 

Maybe a real good thing that there is a halt to this setting up sda5 access !!
Look, is sda5 a partition that contains a operating system ? Rather than just a storage partition ?
I have had the time to consider what is, rather than what you think you want. IF this is a operating system partition, changing the ownership of all the files will be very very bad ! and there will be no recovery from such an action to the operating system ! .. consider well what you are asking . 
We DO NOT want to change the ownership of a operating system at large ! ( ! sudo chown -R javier:javier /mnt/steam-files )

Depending on what is .. One can set up a shared directory in the sda5 partition for steam files to be copied to. This shared directory may meet your needs and requirements ?

[INDENT][INDENT]think 3 times
[INDENT][INDENT][INDENT]act once !
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by javierdl on 2016-10-11
Hi Bashing-om,

You must be right. I believe I have Ubuntu Studio there. But I no longer need it. Maybe I should first format that partition, right?

---

### Post by Bashing-om on 2016-10-11
javierdl; Uh Huh !

A dedicated storage partition is a great idea !
Again, a lot of thought in how you want to use/set-up the partition(s) is time well spent.

Me I am always of the mind if I do not use it - have no need of it ..... get rid of it .

[INDENT][INDENT]keep it clean behind me
[/INDENT][/INDENT]

---

### Post by javierdl on 2016-10-11
Never mind about this post...
I didn't realize we were at the second page already ;)

Should an Admin want to remove this post altogether that's ok with me.
--------------------------------------------------------------------------

Hi Bashing-om,

You're right! There is Ubuntu Studio installed (I forgot). But I no longer need it. 
I suppose I could just format that partition and try again, right?

---

### Post by Bashing-om on 2016-10-11
javierdl; Hey ;

> **javierdl said:**
> Never mind about this post...
I didn't realize we were at the second page already ;)

Should an Admin want to remove this post altogether that's ok with me.
--------------------------------------------------------------------------

Hi Bashing-om,

You're right! There is Ubuntu Studio installed (I forgot). But I no longer need it. 
I suppose I could just format that partition and try again, right?

My post #12 refers :

Sure If ya want you can reformat the drive and set up storage partition(s); It is your system to suite your use case.

[INDENT][INDENT]it's buntu
[INDENT][INDENT][INDENT]you can have it your way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by javierdl on 2016-10-11
Hey Bashing-om!
Cool! I'll do just that then. And try the same commands you kindly shared before.


JDL
P.S. I like your writing style. Are you a writer by any chance?

---

### Post by Bashing-om on 2016-10-11
javierdl; Good deal ..

If ya get stuck, we are here .
-------------------
off topic:
> 
P.S. I like your writing style. Are you a writer by any chance?


Not hardly ! .. My communications skills reek . I know that and I work real hard on improving - When writing I have the time to consider not only what I want to convey, but how . ( and add a bit of humor to lighten the load )

[INDENT][INDENT]choose wisely
[INDENT][INDENT]sometimes you only get the one shot
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by javierdl on 2016-10-12
I formatted sda5 to ext4.
Then I went back to your commands. In the end (of this attempt), it gave me an error when trying to edit the fstab file, again. Have a look:

```
javier@javier-Predator-G3-710:~$ sudo mkdir /mnt/steam-files[sudo] password for javier: 
mkdir: cannot create directory &#8216;/mnt/steam-files&#8217;: File exists
javier@javier-Predator-G3-710:~$ sudo mount /dev/sda5 /mnt/steam-files
javier@javier-Predator-G3-710:~$ ls -al /mnt/steam-files
total 8
drwxr-xr-x 2 root root 4096 Oct 11 10:13 .
drwxr-xr-x 3 root root 4096 Oct 11 10:13 ..
javier@javier-Predator-G3-710:~$ sudo umount /dev/sda5
umount: /dev/sda5: not mounted
javier@javier-Predator-G3-710:~$ sudo cp /etc/fstab etc/fstab-12Oct2016
cp: cannot create regular file 'etc/fstab-12Oct2016': No such file or directory
javier@javier-Predator-G3-710:~$ sudo -H gedit /etc/fstab
sudo parted -l


** (gedit:5422): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported
javier@javier-Predator-G3-710:~$ sudo parted -l
Model: ATA WDC WD10EZEX-21M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system     Name  Flags
 1      1049kB  538MB   537MB   fat32           EF    boot, esp
 5      538MB   301GB   300GB   ext4
 2      301GB   615GB   315GB   fat32                 msftdata
 3      615GB   992GB   377GB   fat32                 msftdata
 4      992GB   1000GB  8523MB  linux-swap(v1)        diag




Model: ATA Patriot Torch LE (scsi)
Disk /dev/sdb: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system     Name  Flags
 1      1049kB  211MB   210MB   fat32                 boot, esp
 2      211MB   228MB   16.8MB  ext4            Mi    msftres
 3      228MB   1026MB  799MB   ntfs                  msftdata
 4      1026MB  88.6GB  87.6GB  ntfs                  msftdata
 6      88.6GB  109GB   20.8GB  ext4
 7      109GB   110GB   386MB   linux-swap(v1)
 8      110GB   120GB   10.3GB  ext4




Model: TOSHIBA External USB 3.0 (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start  End     Size    Type     File system  Flags
 1      106MB  2000GB  2000GB  primary  ntfs




javier@javier-Predator-G3-710:~$ sudo fdisk -lu
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 1B1FA484-E02B-4FAA-906D-10D3D588B00B


Device          Start        End   Sectors   Size Type
/dev/sda1        2048    1050623   1048576   512M EFI System
/dev/sda2   586989568 1201389567 614400000   293G Microsoft basic data
/dev/sda3  1201389568 1936877567 735488000 350.7G Microsoft basic data
/dev/sda4  1936877568 1953523711  16646144     8G Windows recovery environment
/dev/sda5     1050624  586989567 585938944 279.4G Linux filesystem


Partition table entries are not in disk order.




Disk /dev/sdb: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: A62FCAC7-9491-47C0-BE48-46384F1AD03B


Device         Start       End   Sectors   Size Type
/dev/sdb1       2048    411647    409600   200M EFI System
/dev/sdb2     411648    444415     32768    16M Microsoft reserved
/dev/sdb3     444416   2004319   1559904 761.7M Microsoft basic data
/dev/sdb4    2004320 173001607 170997288  81.6G Microsoft basic data
/dev/sdb6  173002752 213577727  40574976  19.4G Linux filesystem
/dev/sdb7  213577728 214331391    753664   368M Linux swap
/dev/sdb8  214331392 234440703  20109312   9.6G Linux filesystem








Disk /dev/sdc: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x545e75e9


Device     Boot  Start        End    Sectors  Size Id Type
/dev/sdc1       206848 3907024064 3906817217  1.8T  7 HPFS/NTFS/exFAT
javier@javier-Predator-G3-710:~$ sudo blkid -c /dev/null -o list
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  vfat             (not mounted)  D45B-1044
/dev/sda2  vfat             (not mounted)  5968-2E1F
/dev/sda3  vfat             (not mounted)  5999-D4D5
/dev/sda4  swap             (not mounted)  e863d0f6-0ab2-4f1f-9fa3-55a652b02283
/dev/sda5  ext4             (not mounted)  3ff8f52b-26d0-415f-b890-9ed186c00c5b
/dev/sdb1  vfat             /boot/efi      A023-0678
/dev/sdb2  ext4             (not mounted)  fb4b6aab-3aa9-4f22-ac08-957d3765f525
/dev/sdb3  ntfs             (not mounted)  01D21F5BB33EFBA0
/dev/sdb4  ntfs    Win10    (not mounted)  7B637EED5EAE730B
/dev/sdb6  ext4             /              649ff9fc-1a34-4427-9ca4-9310bff5963a
/dev/sdb7  swap             [SWAP]         db1e3a9e-cd9d-48de-8e42-e674b4fdb699
/dev/sdb8  ext4             /home          1c6d2b39-7de5-4e00-a7d4-7e237fb789f8
/dev/sdc1  ntfs    TOSHIBA  /media/javier/TOSHIBA A46CE4BB6CE488FE
javier@javier-Predator-G3-710:~$ sudo mkdir /mnt/steam-files
mkdir: cannot create directory &#8216;/mnt/steam-files&#8217;: File exists
javier@javier-Predator-G3-710:~$ sudo mount /dev/sda5 /mnt/steam-files
javier@javier-Predator-G3-710:~$ ls -al /mnt/steam-files
total 8
drwxr-xr-x 2 root root 4096 Oct 11 10:13 .
drwxr-xr-x 3 root root 4096 Oct 11 10:13 ..
javier@javier-Predator-G3-710:~$ sudo umount /dev/sda5
umount: /dev/sda5: not mounted
javier@javier-Predator-G3-710:~$ sudo cp /etc/fstab /etc/fstab-12Oct2016
javier@javier-Predator-G3-710:~$ sudo -H gedit /etc/fstab


(gedit:5781): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files


** (gedit:5781): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-spell-enabled not supported


** (gedit:5781): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-encoding not supported


** (gedit:5781): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported
javier@javier-Predator-G3-710:~$ 



```

---

### Post by Bashing-om on 2016-10-12
javierdl; Hokay ..

In small steps .. one at a time.

> 
mkdir: cannot create directory ‘/mnt/steam-files’: File exists

a true statement as you had made that directory formerly in that 1st setup.
The mount point exists, so we move on .

> 
umount: /dev/sda5: not mounted

No idea what transpired here as it was mounted when you ran " ls -al /mnt/steam-files " gave positive output. Maybe, unmounted in the GUI ?

> 
cp: cannot create regular file 'etc/fstab-12Oct2016': No such file or directory

again a true statement. In that the correct path for the copy target must be given : There is no such path as 'etc' . The path is given from '/' (root) .. such that the leading '/' is crucial ! // The path becomes " /etc/fstab-12Oct2016 .


> 
** (gedit:5422): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported

Not have gedit installed as the default editor ??? I am not looking over your shoulder, I can only advise as to what you tell me .. Is this Desktop (l)ubuntu ? such that the default text editor is LeavPad ?? Or some other ? Adjust the editor to what you have on your system .

Edit the file after you have made the back up.

As you have made up a new partition for steam-files .. the UUID will now be different that that provided. Will require changing the UUID in /etc/fstab to reflect what is now assigned to the new partition.
```

sudo blkid -c /dev/null -o list

```

Clear as mud ?

[INDENT][INDENT][INDENT]carry on
[INDENT][INDENT][INDENT]my wayward son
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by javierdl on 2016-10-12
Hey Bashing-om! :)


Actually, it is pretty clear.
I did find my new identifier. 
Went through the commands again, I found that the same 2-lines command I had to add to fstab was still there from the previous attempt (with the new identifier). 
But I'm still getting that "(edit:5126): tk-Warning **" error when trying to edit the fstab file :(
Does this mean that gedit is not my default text editor? Is that it?
Gedit is my default text editor. So I don't get it. 
Am I supposed to do something else to officially declare it my default t.e. ?

Thanks Bashing-om

JDL

---

### Post by Bashing-om on 2016-10-12
javierdl; Hey ..

Got me ... as to the default text editor on your system.

What returns:
```

dpkg -l gedit

```
Then again perhaps we have something going on with the hand shaking protocol to establish permissions ?
we can change that protocol; Or the means to invoke the default text editor with admin authority ( sudoedit ). 

[INDENT]'buntu
[INDENT][INDENT][INDENT]says safety is no accident
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by javierdl on 2016-10-12
Hi Bashing-om,

```
dpkg -l geditDesired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  gedit          3.18.3-0ubun amd64        official text editor of the GNOME



```

---

### Post by Bashing-om on 2016-10-12
javierdl; Welp. 

gedit is installed .
As when executing " sudo -H gedit /etc/fstab " the terminal outputs are warnings, NOT errors .
No idea of what metadata might be "missing" .
I bet the file opens as expected, and that you can make the edits - and save the file .

Try and advise -
after the edit and save .. have a look/check :
```

cat /etc/fstab

```

In my use case - gedit wants some icon themes that I have no intention of installing :
> 
 sysop@1404mini:~$ sudo -H gedit /etc/fstab
[sudo] password for sysop: 
You can't get the wood, you know.
[sudo] password for sysop: 

** (gedit:3051): WARNING **: Could not load theme icon user-bookmarks-symbolic: Icon 'user-bookmarks-symbolic' not present in theme

** (gedit:3051): WARNING **: Could not load theme icon user-home-symbolic: Icon 'user-home-symbolic' not present in theme

** (gedit:3051): WARNING **: Could not load theme icon drive-harddisk-symbolic: Icon 'drive-harddisk-symbolic' not present in theme
sysop@1404mini:~$

these warnings have no impact on the functionality of gedit .

[INDENT][INDENT][INDENT]good to go ?
[/INDENT][/INDENT][/INDENT]

---

### Post by javierdl on 2016-10-12
I see.
Correct, even with those warnings, gedit has successfully saved the changes.

Then, since the fstab file looks good (right?). I can safely continue with the next commands (right?).

```
cat /etc/fstab# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=649ff9fc-1a34-4427-9ca4-9310bff5963a /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
#UUID=A023-0678  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/sda8 during installation
UUID=1c6d2b39-7de5-4e00-a7d4-7e237fb789f8 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=db1e3a9e-cd9d-48de-8e42-e674b4fdb699 none            swap    sw              0       0
UUID=A023-0678    /boot/efi    vfat    defaults    0    1
#mountpoint for sda5 steam-files added 11Oct2016
UUID=3ff8f52b-26d0-415f-b890-9ed186c00c5b /mnt/steam-files            ext4    defaults        0       2


```

The next commands are:

[B]sudo mount -a
sudo chown -R javier:javier /mnt/steam-files
ls -al /mnt/steam-files[/B]

---

### Post by Bashing-om on 2016-10-12
javierdl; Uh Huh .

If
confirms to me :
```

sudo blkid -c /dev/null -o list

```
comes back that sad5 has the UUID of " 3ff8f52b-26d0-415f-b890-9ed186c00c5b "

Then
Yeah carry on.

[INDENT][INDENT]with you 'til the end
[/INDENT][/INDENT]

---

### Post by javierdl on 2016-10-12
Success has been attained! (thanks to you, Bashing-om!!)
The Steam files for Left4Dead2 are being downloaded right into /mnt/steam-files as we speak!
I can't wait to run the game to confirm that it installed good. But I suppose it's safe enough to think that it'll work.

So thank you ever so much for ALL your AMAZING AND PATIENT HELP, Bashing-om :)

I would imagine that I'll need your magic commands again in the future, so they are going directly into my personal OneNote collection of Linux commands ;)

JDL

---

### Post by Bashing-om on 2016-10-12
javierdl; Outstanding !

I hope you enjoyed the ride .

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

And I look forward to our next adventure .

[INDENT][INDENT]see it was
[INDENT][INDENT][INDENT]nothing but a thing
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by javierdl on 2016-10-12
LOL
Yes, I did enjoy the ride. It was particularly rewarding :)

Thank you kindly, again! :)

Also looking forward to the next one.

---

### Post by javierdl on 2017-01-02
I hope people are still checking this thread...

To better understand "Permissions/Modes", I wanted to ask the following:
In this thread, pag 1, [post #8]("https://ubuntuforums.org/showthread.php?t=2339524&p=13555136#post13555136"), Bashing-om advised me, (among the best no doubt!, and he's writing is fun to read too!) among the various commands he advised, he wrote: 
```
sudo chown -R javier:javier /mnt/steam-files
```

Now, SeijiSensei, (another amazing advisor), from a different thread (Can I have more than one owner for one mount point?), this [post #6]("https://ubuntuforums.org/showthread.php?t=2347324&p=13586452#post13586452"), advised:
```
cd /path/to/the/mount/point
sudo chown you:yourgroup . -R
sudo chmod 775 you:yourgroup -R
```

As you can see both commands advises are about "permissions" (on a given mount point). However, the 2nd example uses also the "[chmod]("http://www.computerhope.com/unix/uchmod.htm")" command. I do understand how chmod is used. But the actual question is: 
Why was it not needed on the 1st example? 
Maybe due to their respective circumstances? 
Or maybe it could have been added anyway?

---

### Post by Keith_Helms on 2017-01-02
There are some cases where files have the right owner and the wrong permissions and other cases where files have the right permissions, but the wrong owner.  It's as simple as that.

---

### Post by javierdl on 2017-01-02
I see.
Hence, ownership was the only one thing that was needed for that purpose.
Thanks KH :)

Once more thing actually...

So far these permissions seem to be applied the same to groups", "users", or "mount points". Is this right?

JDL

---

### Post by Keith_Helms on 2017-01-03
> **javierdl said:**
> I see.
Hence, ownership was the only one thing that was needed for that purpose.
Thanks KH :)

Once more thing actually...

So far these permissions seem to be applied the same to groups", "users", or "mount points". Is this right?

JDL

Permissions apply to folders and files.  A mount point is just another folder.  Folders and files have an owner (a user) and a group associated with them and the permissions apply to the owner, the group, and other (any other user).

Here's an excerpt from ls -l done against / on my system:
```
drwxr-xr-x  22 keith keith  4096 Dec 26 15:30 data2
drwxr-xr-x  19 root  root   4800 Jan  2 20:11 dev
```

data2 is a directory I created to use as a mount point.  You can tell it's a directory by the "d" at the front of the permission string.  "keith keith" and "root root" are 2 userids each followed by 2 group names.  In case you haven't noticed yet, whenever you create a user on Ubuntu an identical group name is also created.

EDIT: Just in case I wasn't clear, the permission string applies to that file or folder only.  It does not control what that user or group can do to any other file or folder, except that to read a file within a folder you need to have read authority on both the folder and file and the same goes for write authority.

The permission string starts with a "d" if it's a folder and you will sometimes see other letters at the beginning, like "l" for a link.  The next 9 characters consist of 3 groups of 3 letters or dashes.  rwx stands for read, write, or execute authority.  The 3 groups apply to the owner, the group, and other respectively.  If that owner, group, or other has read, write, or execute authority, the letter will appear.  If they do not, a dash will instead appear.

The chown command is used to change what user and/or group owns the file or folder.  It does NOT change permissions.

The chmod command is used to change the permissions for files or folders.  It does NOT change the owner or group.

Hopefully this will explain a bit the user, group, and permission concepts.  I apologize if I'm telling you things you already knew.

---

### Post by javierdl on 2017-01-03
Thanks a bunch for all the complete explanation KH :)

I applied Bashing-om command lines to 2 other partitions. I created their respective mount points, added them to the fstab file. 
Everything was fine except for one thing: For the 2nd partition, claiming ownership did not work. 
```
javier@javier-Predator-G3-710:/mnt/315gb$ sudo chown javier:3ofus /mnt/315gb
[sudo] password for javier: 
chown: changing ownership of '/mnt/315gb': Operation not permitted
```

I unmounted that partition from a different user, and logged off of my account. When I went back in, I attempted it again. This time it looked as if it had worked, but when I checked the ownership with "sudo ls -al /mnt/315gb", it still showed root ownership :(
The main difference between both partitions, is that for 315gb, its filesystem type is vfat, whereas the 1st one, is ext4.
Is the reason why I can't claim ownership? Because the filesystem type has to be ext4?

Thanks again

---

### Post by Keith_Helms on 2017-01-03
Yes, that's correct.  It's because it's vfat.

Read here:

[http://askubuntu.com/questions/96923/how-do-i-change-permissions-on-a-fat32-formatted-drive/96929#96929](http://askubuntu.com/questions/96923/how-do-i-change-permissions-on-a-fat32-formatted-drive/96929#96929)

---

### Post by javierdl on 2017-01-03
Thank you for confirming that KH, at least now I know what's the next step.
I found some good leads on some software to allow me to access my ext4 partition from Win10 later ;)

JDL

---

### Post by javierdl on 2017-01-04
I was just realising, when I first plugged this HD to the pc, Ubuntu had no problem loading the partitions. Whether they were ext4 or vfat/fat32. More over, I had no problem copying/erasing/creating files into the vfat partition. In fact, the only reason I bothered creating a group/mount point was because Ubuntu would only allow it to be mounted with one user at a time. But then, [B]why was I able to copying/erasing/creating files into the vfat partition?

[/B]I don't suppose it is related, but I found this fstab file in /home:```
line for mounting the external drive
UUID=D04A-0AE4   /media/hdd  exfat   rw,uid=1000,gid=1000,user,exec,umask=003,blksize=4096   0   0

```

Funny thing is, none of my partitions have that UUID, or are called "hdd". I wonder where it came from...

---

### Post by Keith_Helms on 2017-01-04
A UUID string is associated with each partition.  It's better to identify a partition in fstab using UUID than something like /dev/sda1 because that /dev/sd.. identifier might change if you add another drive to the system.  You can see the UUIDs for your partitions by doing
```
ls -l /dev/disk/by-uuid
or
sudo blkid
```

As for why you can or can't write to the vfat volume, I think that is controlled by the permissions on the folder that you mounted it under.

---

