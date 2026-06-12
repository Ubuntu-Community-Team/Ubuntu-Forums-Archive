---
title: "No OS, grub rescue&gt;"
date: 2012-11-16
forum: General Help
---

### Post by Mikhail Weiss on 2012-11-16
[FONT=Verdana, sans-serif][SIZE=2]Hiya, all:[/SIZE][/FONT] 

 [FONT=Verdana, sans-serif][SIZE=2]I'm a relatively neophyte Linux user, and I've been running 64-bit LTS Ubuntu 10.04, only occasionally updating every once in a while when I tired of the nagging update announcements.[/SIZE][/FONT]
 

 [FONT=Verdana, sans-serif][SIZE=2]Well, it seems the most recent update has likely killed the OS. Now, when I boot up the computer, all I see on the black screen is this white text:[/SIZE][/FONT]
 

 [FONT=Verdana, sans-serif][SIZE=2]**error: unknown filesystem.**[/SIZE][/FONT]
 [FONT=Verdana, sans-serif][SIZE=2]**grub rescue>**[/SIZE][/FONT]
 

 [FONT=Verdana, sans-serif][SIZE=2]Using another computer, I downloaded Boot-Repair, as described on this page...[/SIZE][/FONT]
 [FONT=Verdana, sans-serif][[SIZE=2]https://help.ubuntu.com/community/Boot-Repair[/SIZE]]("https://help.ubuntu.com/community/Boot-Repair")[/FONT]
 [FONT=Verdana, sans-serif][SIZE=2]...and burned it to a CD.[/SIZE][/FONT]
 

 [FONT=Verdana, sans-serif][SIZE=2]When I boot from this CD, it gets to this point, “Scanning system (os-prober),” only to then tell me, “No OS has been found on this computer.” The text file it then generates to otherwise describe what it found is cut-n-pasted, below, after this message.[/SIZE][/FONT]
 

 [FONT=Verdana, sans-serif][SIZE=2]Since the output asks that it be reported to [EMAIL="yannubuntu@gmail.com"]yannubuntu@gmail.com[/EMAIL], I did so, but I also post it here in case someone has some swell ideas that will get the computer up and running once again. [/SIZE][/FONT] 
 

 [FONT=Verdana, sans-serif][SIZE=2]Any assistance will be greatly appreciated.[/SIZE][/FONT]
 

 [FONT=Verdana, sans-serif][SIZE=2]Thanks bunches,[/SIZE][/FONT]
 [FONT=Verdana, sans-serif][SIZE=2]Mikhail Weiss[/SIZE][/FONT]
 
```

 - ------------------ -
 START TEXT FILE
 - ------------------ -
 

      Boot Info Script 0.61.full + Boot-Repair extra info      [Boot-Info September 18th 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.

sda1: __________________________________________________________________________

   File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

   File system:       Extended Partition
    Boot sector type:  -
   Boot sector info: 

sda5: __________________________________________________________________________

   File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048 1,932,769,279 1,932,767,232  83 Linux
/dev/sda2       1,932,771,326 1,953,523,711    20,752,386   5 Extended
/dev/sda5       1,932,771,328 1,953,523,711    20,752,384  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda5        cdccf3f4-5dd6-4713-a894-0901734db499   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sr0         /live/image              iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000080  63 6f 6e 74 72 6f 6c 2d  63 65 6e 74 65 72 32 2e  |control-center2.|
00000090  73 76 67 00 aa 8b e8 02  20 00 17 01 67 6e 6f 6d  |svg..... ...gnom|
000000a0  65 2d 70 6f 77 65 72 2d  6d 61 6e 61 67 65 72 2e  |e-power-manager.|
000000b0  73 76 67 00 e6 46 e8 02  18 00 10 07 78 66 73 6d  |svg..F......xfsm|
000000c0  2d 73 75 73 70 65 6e 64  2e 73 76 67 c6 45 e8 02  |-suspend.svg.E..|
000000d0  18 00 10 07 6b 65 79 5f  62 69 6e 64 69 6e 67 73  |....key_bindings|
000000e0  2e 73 76 67 f1 8a e8 02  50 00 1b 01 6e 6d 2d 73  |.svg....P...nm-s|
000000f0  74 61 67 65 30 33 2d 63  6f 6e 6e 65 63 74 69 6e  |tage03-connectin|
00000100  67 30 32 2e 73 76 67 61  2b 8b e8 02 2c 00 24 01  |g02.svga+...,.$.|
00000110  6e 6d 2d 73 74 61 67 65  30 31 2d 63 6f 6e 6e 65  |nm-stage01-conne|
00000120  63 74 69 6e 67 30 38 2e  73 76 67 2e 64 70 6b 67  |cting08.svg.dpkg|
00000130  2d 6e 65 77 a4 8b e8 02  14 00 0c 01 73 79 6e 61  |-new........syna|
00000140  70 74 69 63 2e 73 76 67  1e 46 e8 02 54 00 1f 07  |ptic.svg.F..T...|
00000150  73 79 73 74 65 6d 2d 63  6f 6e 66 69 67 2d 73 65  |system-config-se|
00000160  63 75 72 69 74 79 6c 65  76 65 6c 2e 73 76 67 02  |curitylevel.svg.|
00000170  e1 8a e8 02 2c 00 24 01  6e 6d 2d 73 74 61 67 65  |....,.$.nm-stage|
00000180  30 33 2d 63 6f 6e 6e 65  63 74 69 6e 67 30 39 2e  |03-connecting09.|
00000190  73 76 67 2e 64 70 6b 67  2d 6e 65 77 a2 8b e8 02  |svg.dpkg-new....|
000001a0  24 00 1b 01 6e 6d 2d 73  74 61 67 65 30 32 2d 63  |$...nm-stage02-c|
000001b0  6f 6e 6e 65 63 74 69 6e  67 30 35 2e 73 76 67 01  |onnecting05.svg.|
000001c0  af 46 e8 02 20 00 15 07  61 70 70 6c 69 63 61 74  |.F.. ...applicat|
000001d0  69 6f 6e 2d 78 2d 76 6e  63 2e 73 76 67 00 00 00  |ion-x-vnc.svg...|
000001e0  8c 45 e8 02 1c 00 12 07  73 75 73 65 68 65 6c 70  |.E......susehelp|
000001f0  63 65 6e 74 65 72 2e 73  76 67 00 00 86 46 e8 02  |center.svg...F..|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc 

=============================== StdErr Messages: ===============================

File descriptor 7 (pipe:[6403]) leaked on lvscan invocation. Parent PID 10126: bash
File descriptor 8 (pipe:[6403]) leaked on lvscan invocation. Parent PID 10126: bash
  No volume groups found
mdadm: No arrays found in config file or automatically

ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-11-16__16h13 ===================
boot-repair version : 3.193-0ppa22~lucid
boot-sav version : 3.193-0ppa39~lucid
glade2script-gtk2 version : 0.0.1-0ppa4~lucid
boot-sav-nonfree version :
Please connect internet. Then close this window.
/usr/share/boot-sav/gui-update.sh: line 77: add-apt-repository: command not found
/usr/share/boot-sav/gui-update.sh: line 77: add-apt-repository: command not found
deb [http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu](http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu) lucid main
/usr/share/boot-sav/gui-update.sh: line 77: add-apt-repository: command not found
/usr/share/boot-sav/gui-update.sh: line 77: add-apt-repository: command not found
deb [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) lucid main
W: Failed to fetch [http://cdn.debian.net/debian/dists/squeeze/Release.gpg](http://cdn.debian.net/debian/dists/squeeze/Release.gpg)  Could not resolve 'cdn.debian.net'

W: Failed to fetch [http://cdn.debian.net/debian/dists/squeeze/main/i18n/Translation-en.bz2](http://cdn.debian.net/debian/dists/squeeze/main/i18n/Translation-en.bz2)  Could not resolve 'cdn.debian.net'

W: Failed to fetch [http://cdn.debian.net/debian/dists/squeeze/main/i18n/Translation-en_US.bz2](http://cdn.debian.net/debian/dists/squeeze/main/i18n/Translation-en_US.bz2)  Could not resolve 'cdn.debian.net'

W: Failed to fetch [http://security.debian.org/dists/squeeze/updates/Release.gpg](http://security.debian.org/dists/squeeze/updates/Release.gpg)  Could not resolve 'security.debian.org'

W: Failed to fetch [http://security.debian.org/dists/squeeze/updates/main/i18n/Translation-en.bz2](http://security.debian.org/dists/squeeze/updates/main/i18n/Translation-en.bz2)  Could not resolve 'security.debian.org'

W: Failed to fetch [http://security.debian.org/dists/squeeze/updates/main/i18n/Translation-en_US.bz2](http://security.debian.org/dists/squeeze/updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.debian.org'

W: Failed to fetch [http://cdn.debian.net/debian/dists/squeeze-updates/Release.gpg](http://cdn.debian.net/debian/dists/squeeze-updates/Release.gpg)  Could not resolve 'cdn.debian.net'

W: Failed to fetch [http://cdn.debian.net/debian/dists/squeeze-updates/main/i18n/Translation-en.bz2](http://cdn.debian.net/debian/dists/squeeze-updates/main/i18n/Translation-en.bz2)  Could not resolve 'cdn.debian.net'

W: Failed to fetch [http://cdn.debian.net/debian/dists/squeeze-updates/main/i18n/Translation-en_US.bz2](http://cdn.debian.net/debian/dists/squeeze-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'cdn.debian.net'

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/Release.gpg)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/main/i18n/Translation-en.bz2)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/Release.gpg)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/main/i18n/Translation-en.bz2)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Could not resolve 'ppa.launchpad.net'

W: Some index files failed to download, they have been ignored, or old ones used instead.

0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 63 not upgraded.
WARNING: The following packages cannot be authenticated!
os-uninstaller
Err [http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/](http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/) lucid/main os-uninstaller all 3.18-0ppa13~lucid
Could not resolve 'ppa.launchpad.net'
Failed to fetch [http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/pool/main/o/os-uninstaller/os-uninstaller_3.18-0ppa13~lucid_all.deb](http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/pool/main/o/os-uninstaller/os-uninstaller_3.18-0ppa13~lucid_all.deb)  Could not resolve 'ppa.launchpad.net'
E: Some files failed to download

0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 63 not upgraded.
WARNING: The following packages cannot be authenticated!
boot-repair
Err [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/) lucid/main boot-repair all 3.193-0ppa22~lucid
Could not resolve 'ppa.launchpad.net'
Failed to fetch [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/pool/main/b/boot-repair/boot-repair_3.193-0ppa22~lucid_all.deb](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/pool/main/b/boot-repair/boot-repair_3.193-0ppa22~lucid_all.deb)  Could not resolve 'ppa.launchpad.net'
E: Some files failed to download
File descriptor 7 (pipe:[6403]) leaked on lvs invocation. Parent PID 4174: /bin/sh
File descriptor 8 (pipe:[6403]) leaked on lvs invocation. Parent PID 4174: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 18.07.2012, squeeze, Debian, x86_64)
CPU op-mode(s):        64-bit
initrd=/live/initrd2.img boot=live config   quiet BOOT_IMAGE=/live/vmlinuz2

=================== os-prober:


=================== blkid:
/dev/sda5: UUID="cdccf3f4-5dd6-4713-a894-0901734db499" TYPE="swap"
/dev/loop0: TYPE="squashfs"

=================== dmesg | grep EFI :
This live-session is not EFI-compatible.


=================== PARTITIONS & DISKS:



=================== parted -l:

Model: ATA SAMSUNG HD103UJ (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      1049kB  990GB   990GB   primary                   boot
2      990GB   1000GB  10.6GB  extended
5      990GB   1000GB  10.6GB  logical   linux-swap(v1)




  disk label

======== parted -lm:

BYT;
/dev/sda:1000GB:scsi:512:512:msdos:ATA SAMSUNG HD103UJ;
1:1049kB:990GB:990GB:::boot;
2:990GB:1000GB:10.6GB:::;
5:990GB:1000GB:10.6GB:linux-swap(v1)::;

e ro size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  block bsg btrfs-control bus cdrom cdrom1 cdrw cdrw1 char console core cpu_dma_latency disk dri fb0 fd fd0 full fuse fw0 hidraw0 hpet initctl input kmsg log MAKEDEV mcelog md mem net network_latency network_throughput null port ppp psaux ptmx pts random rtc rtc0 scd0 sda sda1 sda2 sda5 sdb sdc sg0 sg1 sg2 sg3 shm snapshot snd sndstat sr0 stderr stdin stdout urandom v4l vga_arbiter video0 xconsole zero
ls /dev/md:

=================== df -Th:

Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    1.7G  7.3M  1.7G   1% /
tmpfs        tmpfs    1.7G     0  1.7G   0% /lib/init/rw
udev         tmpfs    1.7G  224K  1.7G   1% /dev
tmpfs        tmpfs    1.7G     0  1.7G   0% /dev/shm
/dev/sr0   iso9660    339M  339M     0 100% /live/image
tmpfs        tmpfs    1.7G  7.3M  1.7G   1% /live/cow
tmpfs        tmpfs    1.7G     0  1.7G   0% /live
tmpfs        tmpfs    1.7G  8.0K  1.7G   1% /tmp

=================== fdisk -l:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00078e82

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      120310   966383616   83  Linux
/dev/sda2          120310      121602    10376193    5  Extended
/dev/sda5          120310      121602    10376192   82  Linux swap / Solaris


=================== Repair blockers
No OS has been found on this computer. Please report this message to [EMAIL="yannubuntu@gmail.com"]yannubuntu@gmail.com[/EMAIL]

=================== Default settings
Recommended-Repair
This setting would reinstall the  of .

=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.



No change has been performed on your computer. See you soon!
Please connect internet. Then close this window.
 

 - ------------------ -
 END TEXT FILE
 - ------------------ -
```

---

### Post by oldfred on 2012-11-16
Please use code tags, easy to do with highlight like copy and click on # in edit panel above message.

Boot-Repair also should have given a link to post. 

No file system is because there is an issue with sda1. And since sda1 cannot be opened, nothing is found.

We can try filechecks to see if it is repairable.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sda1


I also prefer not to have a monster / (root) partition. And we have seen issues where grub2 does not work on very large root partitions if some files are near beginning of drive and some near end.

I normally suggest 25GB for / (root) and a larger /home. Then depending on what you want perhaps other partitions for other data


But to create more than the standard / & swap you have to use Something else and create the partitions manually.

---

### Post by Mikhail Weiss on 2012-11-17
oldfred:

Thanks for your reply. I posted the same message to yannbuntu, per the instructions in the Boot-Repair output, and he kindly  said this in an email:

[INDENT]Seems like you upgrade (10.04 to 12.04 update) failed, and broke system files. Please fix your system files via an Ubuntu 12.04 disk, this way:[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
[/INDENT]That's a bit of a puzzle to me since I had not intended to upgrade from 10.04 at all, but rather update its various bits and pieces per the nagging "updates are available" popup I usually ignore. :) 

Nonetheless, I'll try that solution unless you think there's a good chance I'll lose the data on the hard drive.

Sorry about my code-posting ignorance, by the way. I'm ignorant about a great many things forum and computer related, but I endeavor to learn.

Meanwhile, I'll try your filecheck instructions to see what happens.

Thanks once again for your assistance.

M.

---

### Post by YannBuntu on 2012-11-17
Hello

Oldfred's suggestion is good, please try it first.

Also, I just saw that you used an old version of Boot-Repair. To update Boot-Repair:
```
sudo apt-get update; sudo apt-get install -y boot-repair boot-sav
```

---

### Post by Mikhail Weiss on 2012-11-18
oldfred:

Thanks for your suggestions. I wasn't sure what to make of this one...

```
#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
```

...so I skipped it and ran this one in the terminal...

```
#e2fsck
```

...which did nothing, so I removed the # and ran it again, as e2fsck, eliciting what appears to be a menu of commands.

Next I ran this one...

```
sudo e2fsck -C0 -p -f -v /dev/sda1
```

...getting this response...

```
e2fsck: Bad magic number in super-block while trying to open /dev/sda1/dev/sda1:
The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
	e2fsck -b 8193<device>
```

...naturally, this is a puzzle to me, but I'm guessing it provides useful information?

Then I ran...

```
sudo e2fsck -f -y -v /dev/sda1
```

...and bunches of this popped up, one after another...

```
Group descriptor [a list of numbers from 6980 to 7372 inserted here in each line] checksum is invalid. FIXED.
```

...followed by this:

```
Pass 1: Checking ionodes, blocks, and size
Deleted inode 10354690 has zero dtime. Fix? Yes
```

This was then followed by these repeating lines...

```
error reading block [numbers here varied once again] (Attempt to read block from filesystem resulted in short read) while getting inode from scan.  Ignore error? Yes

Force rewrite? Yes
```

After bunches of that, this...

```
Free inodes count wrong for group #6112 (8192, counted=3019).
Fix? yes

Directories count wrong for group #6112 (0, counted=744).
Fix? yes

Free inodes count wrong for group #6113 (8192, counted=7851).
Fix? yes

Free inodes count wrong for group #6128 (8192, counted=3453).
Fix? yes

Directories count wrong for group #6128 (0, counted=744).
Fix? yes

Free inodes count wrong for group #6144 (8192, counted=3727).
Fix? yes

Directories count wrong for group #6144 (0, counted=744).
Fix? yes

Free inodes count wrong for group #6160 (8192, counted=4574).
Fix? yes

Directories count wrong for group #6160 (0, counted=744).
Fix? yes

Free inodes count wrong for group #6176 (8192, counted=4709).
Fix? yes

Directories count wrong for group #6176 (0, counted=744).
Fix? yes

Free inodes count wrong for group #6192 (8192, counted=5484).
Fix? yes

Directories count wrong for group #6192 (0, counted=744).
Fix? yes

Free inodes count wrong for group #6208 (8192, counted=3035).
Fix? yes

Directories count wrong for group #6208 (0, counted=744).
Fix? yes

Free inodes count wrong for group #6224 (8192, counted=3188).
Fix? yes

Directories count wrong for group #6224 (0, counted=744).
Fix? yes

Free inodes count wrong for group #6240 (8192, counted=2932).
Fix? yes

Directories count wrong for group #6240 (0, counted=744).
Fix? yes

Free inodes count wrong for group #6256 (8192, counted=4289).
Fix? yes

Directories count wrong for group #6256 (0, counted=744).
Fix? yes

Free inodes count wrong for group #6272 (8192, counted=4813).
Fix? yes

Directories count wrong for group #6272 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6288 (8192, counted=4696).
Fix? yes

Directories count wrong for group #6288 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6304 (8192, counted=2088).
Fix? yes

Directories count wrong for group #6304 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6320 (8192, counted=1910).
Fix? yes

Directories count wrong for group #6320 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6336 (8192, counted=4126).
Fix? yes

Directories count wrong for group #6336 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6352 (8192, counted=5039).
Fix? yes

Directories count wrong for group #6352 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6368 (8192, counted=4368).
Fix? yes

Directories count wrong for group #6368 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6384 (8192, counted=1431).
Fix? yes

Directories count wrong for group #6384 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6400 (8192, counted=162).
Fix? yes

Directories count wrong for group #6400 (0, counted=601).
Fix? yes

Free inodes count wrong for group #6401 (8192, counted=6766).
Fix? yes

Directories count wrong for group #6401 (0, counted=146).
Fix? yes

Free inodes count wrong for group #6416 (8192, counted=2441).
Fix? yes

Directories count wrong for group #6416 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6432 (8192, counted=5572).
Fix? yes

Directories count wrong for group #6432 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6448 (8192, counted=1482).
Fix? yes

Directories count wrong for group #6448 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6464 (8192, counted=5309).
Fix? yes

Directories count wrong for group #6464 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6480 (8192, counted=5455).
Fix? yes

Directories count wrong for group #6480 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6496 (8192, counted=4728).
Fix? yes

Directories count wrong for group #6496 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6512 (8192, counted=3049).
Fix? yes

Directories count wrong for group #6512 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6528 (8192, counted=3537).
Fix? yes

Directories count wrong for group #6528 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6544 (8192, counted=3842).
Fix? yes

Directories count wrong for group #6544 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6560 (8192, counted=5564).
Fix? yes

Directories count wrong for group #6560 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6576 (8192, counted=4111).
Fix? yes

Directories count wrong for group #6576 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6592 (8192, counted=3505).
Fix? yes

Directories count wrong for group #6592 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6608 (8192, counted=3254).
Fix? yes

Directories count wrong for group #6608 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6624 (8192, counted=5314).
Fix? yes

Directories count wrong for group #6624 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6640 (8192, counted=5681).
Fix? yes

Directories count wrong for group #6640 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6656 (8192, counted=2224).
Fix? yes

Directories count wrong for group #6656 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6672 (8192, counted=4322).
Fix? yes

Directories count wrong for group #6672 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6688 (8192, counted=3333).
Fix? yes

Directories count wrong for group #6688 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6704 (8192, counted=5675).
Fix? yes

Directories count wrong for group #6704 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6720 (8192, counted=5975).
Fix? yes

Directories count wrong for group #6720 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6736 (8192, counted=2518).
Fix? yes

Directories count wrong for group #6736 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6752 (8192, counted=2854).
Fix? yes

Directories count wrong for group #6752 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6768 (8192, counted=4728).
Fix? yes

Directories count wrong for group #6768 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6784 (8192, counted=5860).
Fix? yes

Directories count wrong for group #6784 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6800 (8192, counted=2177).
Fix? yes

Directories count wrong for group #6800 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6816 (8192, counted=5865).
Fix? yes

Directories count wrong for group #6816 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6832 (8192, counted=1680).
Fix? yes

Directories count wrong for group #6832 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6833 (8192, counted=7891).
Fix? yes

Free inodes count wrong for group #6848 (8192, counted=5883).
Fix? yes

Directories count wrong for group #6848 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6864 (8192, counted=4046).
Fix? yes

Directories count wrong for group #6864 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6880 (8192, counted=4975).
Fix? yes

Directories count wrong for group #6880 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6896 (8192, counted=3064).
Fix? yes

Directories count wrong for group #6896 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6912 (8192, counted=5923).
Fix? yes

Directories count wrong for group #6912 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6928 (8192, counted=3000).
Fix? yes

Directories count wrong for group #6928 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6944 (8192, counted=4736).
Fix? yes

Directories count wrong for group #6944 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6960 (8192, counted=3095).
Fix? yes

Directories count wrong for group #6960 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6976 (8192, counted=5798).
Fix? yes

Directories count wrong for group #6976 (0, counted=747).
Fix? yes

Free inodes count wrong for group #6992 (8192, counted=2748).
Fix? yes

Directories count wrong for group #6992 (0, counted=747).
Fix? yes

Free inodes count wrong for group #7008 (8192, counted=4488).
Fix? yes

Directories count wrong for group #7008 (0, counted=747).
Fix? yes

Free inodes count wrong for group #7024 (8192, counted=3448).
Fix? yes

Directories count wrong for group #7024 (0, counted=747).
Fix? yes

Free inodes count wrong for group #7040 (8192, counted=5717).
Fix? yes

Directories count wrong for group #7040 (0, counted=747).
Fix? yes

Free inodes count wrong for group #7056 (8192, counted=2348).
Fix? yes

Directories count wrong for group #7056 (0, counted=747).
Fix? yes

Free inodes count wrong for group #7072 (8192, counted=1561).
Fix? yes

Directories count wrong for group #7072 (0, counted=747).
Fix? yes

Free inodes count wrong for group #7088 (8192, counted=5758).
Fix? yes

Directories count wrong for group #7088 (0, counted=747).
Fix? yes

Free inodes count wrong for group #7104 (8192, counted=3280).
Fix? yes

Directories count wrong for group #7104 (0, counted=747).
Fix? yes

Free inodes count wrong for group #7120 (8192, counted=3432).
Fix? yes

Directories count wrong for group #7120 (0, counted=747).
Fix? yes

Free inodes count wrong for group #7136 (8192, counted=3454).
Fix? yes

Directories count wrong for group #7136 (0, counted=747).
Fix? yes

Free inodes count wrong for group #7152 (8192, counted=4019).
Fix? yes

Directories count wrong for group #7152 (0, counted=747).
Fix? yes

Free inodes count wrong for group #7168 (8192, counted=3401).
Fix? yes

Directories count wrong for group #7168 (0, counted=747).
Fix? yes

Free inodes count wrong for group #7184 (8192, counted=3692).
Fix? yes

Directories count wrong for group #7184 (0, counted=747).
Fix? yes

Free inodes count wrong for group #7200 (8192, counted=4252).
Fix? yes

Directories count wrong for group #7200 (0, counted=747).
Fix? yes

Free inodes count wrong for group #7216 (8192, counted=4097).
Fix? yes

Directories count wrong for group #7216 (0, counted=747).
Fix? yes

Free inodes count wrong for group #7232 (8192, counted=3217).
Fix? yes

Directories count wrong for group #7232 (0, counted=747).
Fix? yes

Free inodes count wrong for group #7248 (8192, counted=3937).
Fix? yes

Directories count wrong for group #7248 (0, counted=747).
Fix? yes

Free inodes count wrong for group #7264 (8192, counted=4165).
Fix? yes

Directories count wrong for group #7264 (0, counted=747).
Fix? yes

Free inodes count wrong for group #7280 (8192, counted=3942).
Fix? yes

Directories count wrong for group #7280 (0, counted=747).
Fix? yes

Free inodes count wrong for group #7296 (8192, counted=4011).
Fix? yes

Directories count wrong for group #7296 (0, counted=747).
Fix? yes

Free inodes count wrong for group #7312 (8192, counted=3897).
Fix? yes

Directories count wrong for group #7312 (0, counted=747).
Fix? yes

Free inodes count wrong for group #7328 (8192, counted=3502).
Fix? yes

Directories count wrong for group #7328 (0, counted=747).
Fix? yes

Free inodes count wrong for group #7344 (8192, counted=5209).
Fix? yes

Directories count wrong for group #7344 (0, counted=747).
Fix? yes

Free inodes count wrong for group #7360 (8192, counted=3573).
Fix? yes

Directories count wrong for group #7360 (0, counted=747).
Fix? yes

Free inodes count wrong (60399605, counted=59600399).
Fix? yes


/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****

  799217 inodes used (1.32%)
    1965 non-contiguous files (0.2%)
    1181 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 747845/443/28
112117231 blocks used (46.41%)
       0 bad blocks
      18 large files

  629410 regular files
  106584 directories
      60 character device files
      26 block device files
       0 fifos
     636 links
   63094 symbolic links (50771 fast symbolic links)
      34 sockets
--------
  799844 files
ubuntu@ubuntu:~$ 
```

Does this look useful and informative? I'll try rebooting now to see what happens. Thanks again for the assistance.

Mikhail Weiss

---

### Post by Mikhail Weiss on 2012-11-18
Yann:

Thanks for your reply. I will acquire a new version of Boot-Repair as it looks like it may prove useful for future snafus. I appreciate your reply to my earlier email, and for your post, here, and your willingness to help.:P

Mikhail Weiss

---

### Post by Mikhail Weiss on 2012-11-18
oldfred:

Much to my amazement, your solution appears to have worked. (Not that I doubted you, but rather that I doubted my ability to correctly follow the instructions.) Thank you very much. The computer now boots in what appears to be a perfectly normal fashion.

The Internet connection, however, doesn't appear to work. How do I fix that?

The task bar atop the desktop screen shows a connectivity icon with a red exclamation mark on it. Hovering over the icon indicates, &#8220;No network connection.&#8221; Left-clicking the icon shows a menu consisting of:

**Wired Network** [non-clickable]
disconnected [this is grayed out]
VPN Connections [sub menu consisting of &#8220;Configure VPN...&#8221; and, &#8220;Disconnect VPN...&#8221; [grayed out]]

Right-clicking this same taskbar icon shows a checkmark by &#8220;Enable Networking&#8221; and &#8220;Enable Notifications.&#8221; &#8220;Connection Information&#8221; is grayed out, and clicking on &#8220;Edit connections...&#8221; brings up a dialogue box for Network Connections. Under the Wired tab, under Name, I see, &#8220;Auto eth0,&#8221; and under Last Used, next to &#8220;Auto eth0,&#8221; I see, &#8220;never.&#8221;

Not sure if that information is useful or not, but there it is. Once again, your assistance on fixing this, too, is greatly appreciated.

Mikhail Weiss

---

### Post by YannBuntu on 2012-11-18
Glad you solved your boot problem!
Your internet issue is not linked, so you should mark this thread as [Solved], and open a new thread for the internet issue.

---

### Post by Mikhail Weiss on 2012-11-18
> **YannBuntu said:**
> Glad you solved your boot problem!
Your internet issue is not linked, so you should mark this thread as [Solved], and open a new thread for the internet issue.

Thanks, Yann. I'm glad I (well, oldfred, really) solved the boot problem, too. I'll mark this thread as Solved and will open a new query for the internet connectivity issue, as suggested. I had assumed a relation between the loss of Internet and the boot fixing were related, as the internet connection had never failed before.

Once again, thanks for your assistance.

Mikhail Weiss

---

### Post by oldfred on 2012-11-18
Yann's Boot-Repair is putting me out of business. :) It fixes an awful lot of the most common issues. 

Any line I post with # is just a comment, so you were not supposed to run that line. :)

I am a little concerned on why you have file issues. The most common issue is abnormal shutdown. Some you cannot avoid like power failures. But do not turn power off. Try to do normal shutdown or remember the elephants.

       Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

    
Also in Disk Utility click on drive and see if Smart data is ok. All I really know is green is good, but growing numbers of errors may mean hard drive issues.

Also do not know about Ethernet. If it worked before it should be ok now? Best in new thread.

---

### Post by offgridguy on 2012-11-18
> **oldfred said:**
> Yann's Boot-Repair is putting me out of business. :) It fixes an awful lot of the most common issues. 

Thank you Yann.

---

