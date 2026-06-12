---
title: "Mount error (22) can't boot after update (13.04)"
date: 2013-05-29
forum: General Help
---

### Post by Feelkarma on 2013-05-29
Hi,
I have just updated Ubuntu 13.04 to kernel 3.8.0-22 and I can't boot. I get black screen, a lot of characters running quickly and then a black screen or, lately :

```
* Starting ...
* Starting Mount network filesystems
mount error(22):invalid argument
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
mountall: mount /media/freebox [1623] terminated with status 32
* Starting Samba Winbind
* Stopping Mount Network filesystems
* Startinhg NetBios name server
* Stopping Userspace bootsplash
```

Then cursor blinking, nothing I can do.


Going through the recovery and trying FSCK I get:
```
/dev/sda5: cean, 364086/5906432 files, 8668161/23604736 blocks
mount error(22):invalid argument
```

Can anyone help?
Many thanks

---

### Post by Bashing-om on 2013-05-29
[COLOR=#000000]Feelkarma; Hi !

As a place to start the troubleshooting.... what results when you boot up with the old kernel version ?
[/COLOR][INDENT][COLOR=#000000]
just a process of learning

[/COLOR][/INDENT]

---

### Post by Feelkarma on 2013-05-29
Hi,

Thanks, I did try other versions but same errors.

---

### Post by Bashing-om on 2013-05-29
[COLOR=#000000]Feelkarma;

Well, looks like networking is trying to start (samba says a Windows' network);
Can you access your system through "recovery mode" and choose "root access" ? Maybe from there we can see what is going on. 
[/COLOR][INDENT=2][COLOR=#000000]

strok'n and poke'n[/COLOR][/INDENT]

---

### Post by Feelkarma on 2013-05-30
Hi Bashing-om,
Yes I can, I have tried accessing fstab but (i) I can't get write access when editing it via nano and (ii) I'm not really sure what to do.
Many thanks for your help!

---

### Post by Bashing-om on 2013-05-30
Here is one approach:
go to the rescue mode- root access -  and type the command
```
mount -o remount rw /
```     <-------------mounts "root's" partitions read and write to edit


```
gedit /etc/fstab
```
Now you can edit the file( I mean comment out the problematic lines). After edit save the file !

Reboot :
```
shutdown -r now
``` 

Now you should be able to boot up your system. If ya require an assist to "fix" your fstab file; sure, post it back here and we will have a gander at it.[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by Feelkarma on 2013-05-30
Tanks I will try tonight as I am off to work, that's why I love Ubuntu, help is always available :)

---

### Post by Feelkarma on 2013-05-30
Hi again,
No luck unfortunately, gedit couldn't load as x couldn't launch (maybe an nvidia driver issue?).
Please see below a screenshot of fstab edited with nano, I have commented out the network drives but I still get the same problem:
[IMG]http://edencocoon.com/tmp/2.jpg[/IMG]

The end of the screen I get on startup looks like this:
[IMG]http://edencocoon.com/tmp/1.jpg[/IMG]

Sorry about the screenshots but I can't think of any other way ;)
Many thanks in advance

---

### Post by Bashing-om on 2013-05-30
[COLOR=#000000]Feelkarma; Well, well, well....
You are correct in that if X is not running there is no support for the GUI application "gedit".
Back up and punt, let's see if we can boot ya to a Command Line Interface and get some more info:
[/COLOR]
Try this: Boot up ubuntu from cold boot, soon as the bios screen clears, depress the shift key -> grub menu>Insure a "non recovery" kernel option is highlighted and press the "e"key for edit mode -> boot parameters; arrow down to the line similar to this "linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash"
; arrow across to the term "quiet splash" and delete them ; ctl+x to continue the boot process.
Depending on the version installed other "means/options" might be needed to get the CLI ->
At that CLI "text" login prompt, enter username followed by your pass word - password no response is normal;

Now what happens with terminal code:
```
sudo service lightdm start
``` assuming that you have "unity" as a desk top manager - else advise otherwise- to start X and activate the desktop. Post back any errors.
key combo ctl+alt+f1 returns to the text login tty to see the errors
ctl+alt+f7 takes you back to the GUI desk top 
[INDENT=2]
one small step for man ->>>[/INDENT]

---

### Post by Feelkarma on 2013-05-30
Well all goes well until Ctrl x where I get black screen with blinking cursor but nothing happens even if I try typing username and password...

---

### Post by Feelkarma on 2013-05-30
I also tried sudo service lightdm from root in recovery mode exactly same result

---

### Post by Bashing-om on 2013-05-30
[COLOR=#000000]Feelkarma; Yuk !

OK, let's go back to the original premise of file system corruption.
In order to check a file system, it must not be mounted -> ya got a liveDVD on hand ?
Boot the liveDVD and in terminal:
```
sudo fdisk -lu ##to identify the partitions

```[/COLOR]```
sudo e2fsck -C0 -p -f -v /dev/sda1 ##for a quick looksee
sudo e2fsck -f -y -v /dev/sda1 ##indepth fixes, -y option auto-answers for yes do it[COLOR=#000000]
[/COLOR]
```[COLOR=#000000]
Run "e2fsck" on each partition on your system - less swap, no can do swap.
[/COLOR][INDENT=2][COLOR=#000000]
where do we stand now ?

[/COLOR][/INDENT]

---

### Post by Feelkarma on 2013-05-31
Hi Bashing-om,
I'll make a live USB/DVD tonight, I'm in France so in a different time zone ;)
Many thanks for your help!

---

### Post by Feelkarma on 2013-06-01
Hi again,
So this is what I get with fdisk:

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0f18b93e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   204812684   102406311    7  HPFS/NTFS/exFAT
/dev/sda2       397319580  1953520064   778100242+   7  HPFS/NTFS/exFAT
/dev/sda3       204814334   397318143    96251905    5  Extended
/dev/sda5       204814336   393652223    94418944   83  Linux
/dev/sda6       393654272   397318143     1831936   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b9b22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   966248447   483123200   83  Linux
/dev/sdb2       966250496   976773103     5261304   82  Linux swap / Solaris

Disk /dev/sdc: 7933 MB, 7933526016 bytes
68 heads, 4 sectors/track, 56967 cylinders, total 15495168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        8064    15495167     7743552    c  W95 FAT32 (LBA)
```

Sda1 and sda2 I get this message, as I understand they are NTFS (I have dual boot with windows):

```
e2fsck: Bad magic number in super-block while trying to open /dev/sda1
/dev/sda1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

For sdb5 I get

```
e2fsck: No such file or directory while trying to open /dev/sdb4
Possibly non-existent device?
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sdb5
                                                                               
      364081 inodes used (6.16%, out of 5906432)
         800 non-contiguous files (0.2%)
         731 non-contiguous directories (0.2%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 309212/412
     8668936 blocks used (36.73%, out of 23604736)
           0 bad blocks
           1 large file

      260083 regular files
       30189 directories
          57 character device files
          25 block device files
           0 fifos
          51 links
       73714 symbolic links (54361 fast symbolic links)
           4 sockets
------------
      364123 files
```

For sdc1:

```
       82415 inodes used (0.27%, out of 30195712)
         629 non-contiguous files (0.8%)
          43 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 79740/155
    30392603 blocks used (25.16%, out of 120780800)
           0 bad blocks
           9 large files

       67056 regular files
       12506 directories
           0 character device files
           0 block device files
           0 fifos
           0 links
        2843 symbolic links (2509 fast symbolic links)
           1 socket
------------
       82406 files
```

It seems as nothing is wrong :( 

By the way, this is my fstab:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid                    0  0  
# / was on /dev/sda5 during installation
UUID=f329f22e-6fdd-4921-9fc4-0cb98f01f864  /               ext4  errors=remount-ro                      0  1  
# swap was on /dev/sda6 during installation
UUID=bfcfab25-40a2-4232-b270-728096f7d11c  none            swap  sw                                     0  0  
# swap was on /dev/sdb2 during installation
UUID=bcb5ebe5-5f58-40e9-a096-ca767446374c  none            swap  sw                                     0  0  
# /dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8               0  0  
# /dev/sda2                                  /media/sda2     ntfs  nls=iso8859-1,umask=000,user  0  0  
# //192.168.0.254/Disque\040dur /media/Freebox cifs _netdev,guest,directio,uid=1000,iocharset=utf8,codepage=cp850,file_mode=0777,dir_mode=0777 0 0
# //192.168.0.10/DocsYannis /media/Synology cifs uid=1000,gid=1000,user=*****,pass=***** 0 0
```

Many thanks in advance for your help!

I know the file system is a mess but between the graphic issues (getting proper picture with nvidia issues) the sound issues (trying to get surround sound) and the cpu issues (which had reappeared with 13.04 as I have a Phenom processor which apparently has a driver issue) I can't get bothered to reinstall everything... unless I have to which seems probable now!

---

### Post by Bashing-om on 2013-06-01
[COLOR=#000000]Feelkarma; Hey ;

I am back and I feel for you. (Re-)installing -though often and quick fix - is seldom required. All tools to fix an "LINUX" system exist on that file system, just a matter of determining what tools affect what process.
Now that said...here's the deal...use Windows' tools for Windows' problems, and linux tools for 'buntu situations.

NTFS and W95 FAT32 belong to windows and so ...use Windows' file system checker on these partitions so marked; that verifies their integrity;
ext4 belong to 'buntu ...those partitions - not counting an "extended" partition use ubuntus "e2fsck" tool on --- advisory: extended partitions are not a physical entity that is mearly a "container" for partitions that do have physics[sda3 is the "container" of partitions sda5 and sda6] there is no need to check any partition that is swap, as a swap partition is just space and has no file system.

Now here is the way disks and file partitions are organized.

first disk on your system recognized from the controller bus = sda[/COLOR][INDENT][COLOR=#000000]1st partition on 1st disk = sda1
2nd partition on 1st disk = sda3
[/COLOR][/INDENT]
[COLOR=#000000]second disk recognized = sdb
[/COLOR][INDENT][COLOR=#000000]1st partition in 2nd disk = sdb1
5th partition on 2nd disk = sdb5
[/COLOR][/INDENT]
[COLOR=#000000]and so on  ....
Presently as the concern is to boot up 'buntu we are only concerned with disk drives sda and sdb -> we need to know now where and what partition holds the "root" and is the primary operating system; from "fstab" we have an identifier - the UUID- ;
[/COLOR]> [COLOR=#000000][FONT=Ubuntu Mono]UUID=f329f22e-6fdd-4921-9fc4-0cb98f01f864  / [/FONT][/COLOR]
[COLOR=#000000][where the '/' symbol = root.
[/COLOR][COLOR=#000000] let us match  that UUID to a partition on the system thus:
```
 sudo blkid
```

Now whichever disk correlates to these UUIDs -->in bios, that hard drive is set as the first boot priority.
 
You with me so far ?
---------------
with e2fsck from a liveDVD all ext4 partitions integrity are good;
bios boot priority is set to fstab's UUID
--------------
Try now and boot into ubuntu from a cold boot ::

If you do not now boot, we will be looking at the boot process and see what is going on.
[/COLOR][INDENT=2][COLOR=#000000]
hey, clear as mud ?
 
[/COLOR][/INDENT]

---

### Post by Feelkarma on 2013-06-02
Hi again,
Sorry not sure I understand exactly what I should do, sudo blkid gives the following:

```
/dev/loop0: TYPE="squashfs" 
/dev/loop1: LABEL="casper-rw" UUID="36b17412-6bb6-034d-8e11-c376c42175a3" TYPE="ext2" 
/dev/sda1: UUID="CCE8915CE891459C" TYPE="ntfs" 
/dev/sda2: LABEL="SEC SATA" UUID="3258784658780ABD" TYPE="ntfs" 
/dev/sda5: UUID="f329f22e-6fdd-4921-9fc4-0cb98f01f864" TYPE="ext4" 
/dev/sda6: UUID="bfcfab25-40a2-4232-b270-728096f7d11c" TYPE="swap" 
/dev/sdb1: UUID="5a12ac66-5a69-45f1-90e8-6da3f610fda3" TYPE="ext4" 
/dev/sdb2: UUID="bcb5ebe5-5f58-40e9-a096-ca767446374c" TYPE="swap" 
/dev/sdc1: LABEL="PENDRIVE" UUID="10EE-3929" TYPE="vfat"
```

What should I do next? I assume this means that sda5 is the boot partition?

Getting there :)

---

### Post by Feelkarma on 2013-06-02
Ok, I fixed it, it was an nVidia driver problem.


```
sudo apt-get purge nvidia-current
```

That fixed it, I had to reinstall the drivers and I now have access.

Many thanks for your help!

---

### Post by Bashing-om on 2013-06-02
[COLOR=#000000]Feelkarma; Hey !

Great ya got resolution to the situation.
With proprietary drivers on one's system, many times an update does break things. Recently Nvidia (as of version 304.43) has DKMS - to enable auto-updates - One should be able to enable Nvidia's DKMS when installing the proprietary driver as an option. Might be worth your time to look into it.

For now ... please mark this thread as "solved" as an aid to all searching for a similar solution, as well as keeping the forum organized.
[/COLOR]Interim method:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.
[INDENT=2]
prosper and be well

[/INDENT]

---

### Post by Feelkarma on 2013-06-02
Thanks for your help, I can't find the option to auto update nvidia drivers, where is this option?
I was actually wondering how to switch to solved but couldn't figure it out.
Now I can't get surround sound again but that's for my next post ;)

---

