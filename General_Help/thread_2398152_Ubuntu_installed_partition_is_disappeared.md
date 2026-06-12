---
title: "Ubuntu installed partition is disappeared"
date: 2018-08-08
forum: General Help
---

### Post by luken2 on 2018-08-08
Hello,

My laptop has Windows 10 64bit & Ubuntu 18.04 64bit dual boot system. Few days ago Ubuntu has stucked with  "**[    [COLOR=#008000]OK[/COLOR]    ] Started GNOME Display Manager.t Dispatcher Service.....before the ppp link was shut down....**" It was looks like this > [https://i.stack.imgur.com/K2GlD.jpg](https://i.stack.imgur.com/K2GlD.jpg)

I've tried to fix this with found solutions. Alt+ctrl+f1 or f2 never worked for me on that screen. I tried with fn key. So I ran commands on ubuntu recover mode.

```
sudo apt-get install xdm
sudo dpkg-reconfigure lightdm
sudo apt-get purge gdm
 sudo apt-get install gdm3 ubuntu-desktop

And many. I don't remember other commands.
```

And then It has been ended with this screen. 
[IMG]https://i.stack.imgur.com/w6n3j.jpg[/IMG]

This is not a screenshot of my laptop. But all the the partitions were unknown. Ubuntu installed partition was **sda6**.

With this problem, I couldn't login to ubuntu or win10. Then I tried ubuntu live with my usb. After trying many commands, I was able to log into win10. But ubuntu installed partition is missing.

Win10 also not able to access ubuntu installed partition.

[IMG]https://i.imgur.com/tWKaygs.png[/IMG]

volume 1 :- ubuntu installed partition.

[IMG]https://i.imgur.com/RoAkPoU.png[/IMG]

```


ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/loop0: 1.3 GiB, 1427259392 bytes, 2787616 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xff6f34e2


Device     Boot      Start        End   Sectors   Size Id Type
/dev/sda1  *          2048  209719295 209717248   100G  7 HPFS/NTFS/exFAT
/dev/sda2        209719296  695228415 485509120 231.5G  7 HPFS/NTFS/exFAT
/dev/sda3        695228416 1324374015 629145600   300G  7 HPFS/NTFS/exFAT
/dev/sda4       1324374016 1953523711 629149696   300G  f W95 Ext'd (LBA)
/dev/sda5       1324376064 1710252031 385875968   184G  7 HPFS/NTFS/exFAT
/dev/sda6       1710254080 1919961087 209707008   100G 83 Linux
/dev/sda7       1919969280 1953521663  33552384    16G 82 Linux swap / Solaris








Disk /dev/sdb: 14.9 GiB, 15931539456 bytes, 31116288 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x001576e4


Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *     2048 31116287 31114240 14.9G  c W95 FAT32 (LBA)
ubuntu@ubuntu:~$


```

Please help me. I want to recover my ubuntu os with my data.
Thank you.

---

### Post by ajgreeny on 2018-08-08
Was Windows 10 pre-installed on the machine as I see both hard drives are showing as using legacy ms-dos formatting; Windows 10 pre-installed would have used gtp formatting.

It will be best to see exactly what we are trying to sort out here using a live system if necessary; see **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 **Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by luken2 on 2018-08-08
> **ajgreeny said:**
> Was Windows 10 pre-installed on the machine as I see both hard drives are showing as using legacy ms-dos formatting; Windows 10 pre-installed would have used gtp formatting.

It will be best to see exactly what we are trying to sort out here using a live system if necessary; see **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.     **Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

I'm noob. Sorry to disappoint you. I thought I should tell you about this. I ran default repair before I post this thread. I don't know what change this tool does.

[http://paste.ubuntu.com/p/sbsCXbS6jN/](http://paste.ubuntu.com/p/sbsCXbS6jN/)

Thank you very much for helping me.

---

### Post by oldfred on 2018-08-08
Boot-Repair did not see the Linux partition on sda6, so it just defaulted to installing a Windows type boot loader to MBR.

I might first try fsck on sda6.
       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda6 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda6
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda6

---

### Post by luken2 on 2018-08-08
> **oldfred said:**
> Boot-Repair did not see the Linux partition on sda6, so it just defaulted to installing a Windows type boot loader to MBR.

I might first try fsck on sda6.
       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda6 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda6
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda6

Thank you very much.

sudo parted -l
```

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA TOSHIBA MQ01ABD1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  107GB   107GB   primary   ntfs            boot
 2      107GB   356GB   249GB   primary   ntfs
 3      356GB   678GB   322GB   primary   ntfs
 4      678GB   1000GB  322GB   extended                  lba
 5      678GB   876GB   198GB   logical   ntfs
 6      876GB   983GB   107GB   logical
 7      983GB   1000GB  17.2GB  logical   linux-swap(v1)


Model: Generic- SD/MMC (scsi)
Disk /dev/sdb: 15.9GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  15.9GB  15.9GB  primary  fat32        boot, lba


ubuntu@ubuntu:~$ 

```

sudo e2fsck -C0 -p -f -v /dev/sda6
```

ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda6
e2fsck: Input/output error while trying to open /dev/sda6
/dev/sda6: 
The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

ubuntu@ubuntu:~$ 

```

sudo e2fsck -f -y -v /dev/sda6
```

ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda6 
e2fsck 1.43.5 (04-Aug-2017)
e2fsck: Input/output error while trying to open /dev/sda6

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

ubuntu@ubuntu:~$
```

---

### Post by luken2 on 2018-08-08
Before I turn on and turn off my laptop using live usb drive, this message appears for a second and goes away.

[IMG]https://i.imgur.com/ylbcMMe.jpg[/IMG]

---

### Post by oldfred on 2018-08-08
Did you try the suggested backup super block?

       [http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
List backup superblocks:
sudo dumpe2fs /dev/sda6 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda6

---

### Post by luken2 on 2018-08-09
> **oldfred said:**
> Did you try the suggested backup super block?

       [http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
List backup superblocks:
sudo dumpe2fs /dev/sda6 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda6

```
ubuntu@ubuntu:~$ sudo fsck.ext4 -v /dev/sda6e2fsck 1.43.5 (04-Aug-2017)
fsck.ext4: Input/output error while trying to open /dev/sda6


The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>


ubuntu@ubuntu:~$
```

```
ubuntu@ubuntu:~$ sudo mke2fs -n /dev/sda6mke2fs 1.43.5 (04-Aug-2017)
Creating filesystem with 26213376 4k blocks and 6553600 inodes
Filesystem UUID: 7a21cc20-6441-41ea-9701-52904c9b5bc0
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872


ubuntu@ubuntu:~$
```

```
ubuntu@ubuntu:~$ sudo dumpe2fs /dev/sda6 | grep -i backupdumpe2fs 1.43.5 (04-Aug-2017)
dumpe2fs: Input/output error while trying to open /dev/sda6
ubuntu@ubuntu:~$ 
```

After that I ran, sudo e2fsck -b 32768 /dev/sda6
sudo e2fsck -b 98304 /dev/sda6
sudo e2fsck -b 163840 /dev/sda6
etc
Then I've rebooted. No grub menu so win10 started automatically. Then I tried to access the sda6 using different tools but It wont. Then I rebooted and boot from live usb, same answer ubuntu file manager won't show the sda6.

---

### Post by oldfred on 2018-08-09
Did you get any error messages after running fsck with backup super block?

Since Windows boot loader is in MBR, it is expected that Windows will boot.
You have to repair sda6, so grub can see it and then you can re-install grub to MBR.

But if not repairable, then you have to reformat partition and reinstall Ubuntu, and restore your data from backups.

---

### Post by luken2 on 2018-08-10
> **oldfred said:**
> Did you get any error messages after running fsck with backup super block?

Since Windows boot loader is in MBR, it is expected that Windows will boot.
You have to repair sda6, so grub can see it and then you can re-install grub to MBR.

But if not repairable, then you have to reformat partition and reinstall Ubuntu, and restore your data from backups.

[COLOR=#000000]sudo e2fsck -b 32768 /dev/sda6[/COLOR]
[COLOR=#000000]sudo e2fsck -b 98304 /dev/sda6[/COLOR]
[COLOR=#000000]sudo e2fsck -b 163840 /dev/sda6
[/COLOR]When I ran the command it ask me to press "y" then I keep pressing it. After that each and every commands are end like this.

I want to get back my ubuntu OS with my data if possible. If I can't get OS back, at least I want to get back my data on it. Please help me. Thank you again.

```
ubuntu@ubuntu:~$ sudo e2fsck -b 32768 /dev/sda6
e2fsck 1.43.5 (04-Aug-2017)
ubuntuz was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
.
.
.
--25685235) -(25686016--25690111) -(25853952--25854329) -(25856000--25874624) -(25876480--25906134) -(25907200--25934907) -(25935104--25935615) -(25935872--25937919) -(25938432--25969525) -(25970688--25999631) -(26001408--26035656) -(26036224--26039202) -(26040320--26072985) -(26073088--26077490) -(26079232--26107391) -(26107904--26129287) -(26130432--26166219) -(26167296--26177598) -(26179584--26181631)
Fix<y>? yes
Free blocks count wrong for group #0 (23500, counted=5074).
Fix<y>? yes
Free blocks count wrong for group #1 (31730, counted=286).
Fix<y>? yes
Free blocks count wrong for group #2 (32768, counted=0).
Fix<y>? yes
Free blocks count wrong for group #3 (31730, counted=105).
Fix<y>? yes
Free blocks count wrong for group #4 (32768, counted=0).
Fix<y>? yes
Free blocks count wrong for group #5 (31730, counted=341).
Fix<y>? yes
Free blocks count wrong for group #6 (32768, counted=0).
Fix<y>? yes
Free blocks count wrong for group #7 (31730, counted=724).
Fix<y>?
.
.
.
.
.
Directories count wrong for group #768 (0, counted=2).
Fix? yes


Free inodes count wrong for group #784 (8192, counted=3146).
Fix? yes


Directories count wrong for group #784 (0, counted=691).
Fix? yes


Free inodes count wrong for group #785 (8192, counted=7488).
Fix? yes


Error writing block 1 (Input/output error).  Ignore error? yes




ubuntuz: ***** FILE SYSTEM WAS MODIFIED *****
ubuntuz: 224785/6553600 files (0.8% non-contiguous), 9703313/26213134 blocks
Error writing block 1 (Input/output error).  Ignore error? yes


ubuntu@ubuntu:~$ 



```

---

### Post by oldfred on 2018-08-10
This user ran fsck several times and eventually got data back.
[https://ubuntuforums.org/showthread.php?t=2033778](https://ubuntuforums.org/showthread.php?t=2033778)

Beyond that I cannot suggest anything else.

---

### Post by luken2 on 2018-08-10
> **oldfred said:**
> This user ran fsck several times and eventually got data back.
[https://ubuntuforums.org/showthread.php?t=2033778](https://ubuntuforums.org/showthread.php?t=2033778)

Beyond that I cannot suggest anything else.

Thanks. I'll try. But how do I know it's recovered or not? Partition will appear on ubuntu file manager? If not please tell me. So I can run the commands while checking.

---

### Post by oldfred on 2018-08-10
It should then appear, do not know as I have not had issues.

One time I deleted some data, and learned my lesson to do better backups. So now it is not as critical if I lose a partition or even a drive.

---

### Post by luken2 on 2018-08-10
> **oldfred said:**
> It should then appear, do not know as I have not had issues.

One time I deleted some data, and learned my lesson to do better backups. So now it is not as critical if I lose a partition or even a drive.

Thanks for helping me whole the time.
Yeah I should learn the lesson.

---

### Post by westie457 on 2018-08-13
I once had a SSD that would refuse to boot beyond the Grub Rescue prompt and 'fsck' failed on every superblock.
Not wanting to reinstall I tried an experiment with Testdisk.

This experiment was done on a clean install with no information to lose so if it did not work a reinstall would have been necessary.

It went something like this:
Boot from a live media to try mode
Connect to internet using a cable
Open a terminal and run the following commands ```
sudo apt update # to enable the repos
sudo apt install testdisk
sudo testdisk
```
Accept default suggestion from testdisk for Hard drive, partition table type and analyse
Next do a quick search, when finished select the partitions to restore. Testdisk will say whether or not a partition can be restored.
If all partitions are not found try a 'Deeper Search'  and select each partition to be recovered.
Select 'Write', agree to the prompts and finally reboot for the changes to be recognised.

If successful you will be back to a working system with all files intact.
If unsuccessful then a reinstall of Ubuntu will be necessary.

---

