---
title: "boot partition full"
date: 2017-10-13
forum: General Help
---

### Post by dkolars on 2017-10-13
Have recently encountered this problem...  running 16.04 LTS, 64bit...  Had problems with a HDD, and it messed up my install???  So, re-installed, had more problems, then went to EFI boot from GRUB, now all is working just fine... BUT, getting pop-up messages that this or that can't happen since the disk is full...
I have read about 40+ posts on newsgroups/web about this problem, and none of them seem to apply.  My trash is empty, I only have the last 2 kernels (.35 & .37) in root, can see no deleted but not removed files, etc.  Nothing shows having large files in the boot drive!!  

I've taken screen shots of the Krusader and terminal windows showing the sizes of all directories...  attached them...  Also pic of Gparted view of root drive.

Pics are from last week, today it says I have 0 Mb free, after reboot then have 721.3 Mb free... 

Have no idea why / would use all of a 442 GB drive???
TIA... dk

---

### Post by oldfred on 2017-10-13
You are not showing the separate /boot partition that is a common problem with LVM & encrypted type installs.
You have standard partitions.

What brand/model system.

Some need a boot parameter as they get run-away log files filling drive.

       Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[URL="https://ubuntuforums.org/showthread.php?t=2327570"]https://ubuntuforums.org/showthread.php?t=2327570

[/URL]
 How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 

[URL="https://ubuntuforums.org/showthread.php?t=2327570"]
[/URL]

---

### Post by flocculant on 2017-10-14
[https://ubuntuforums.org/showthread.php?t=1122670](https://ubuntuforums.org/showthread.php?t=1122670)

Check out the "Checking Your Partitions via Terminal" in particular.

should be able to then find your answer to 
>  Have no idea why / would use all of a 442 GB drive???

---

### Post by dkolars on 2017-10-14
oldfred sez:

> You are not showing the separate /boot partition that is a common problem with LVM & encrypted type installs.
You have standard partitions.

What brand/model system.

Some need a boot parameter as they get run-away log files filling drive.

1) Well, this all started when I had to re-install 16.04 and grub quit working... took me 3 tries to get system working at all, and had to use EFI for that to happen.  Had never heard of EFI until this;
2) My system is one I built about 5 yrs ago - ASUS MB, AMD64 6-core CPU, 16Gb RAM;
3)  IF I have log files filling up something somewhere, wouldn't they show up somewhere?  I **never** find large files!

I'm attaching more pics... I re-booted to see what my ASUS number was, and see that I have 2 UEFI drives shown in "Boot Order".  And, my CD drive was not listed 1st, as I always have it.  So, I moved one of the UEFI to the end, moved the CD drive to be 1st rebooted, and went to grub rescue> prompt!  Rebooted, switched UEFI's, rebooted, and again the grub rescue prompt.  Put both UEFI's in place behind the CD drive, rebooted, yep, grub rescue prompt again.  Moved the CD drive to #3, after the UEFI's and boots fine.  I really would like my CD drive to be in 1st place (so to speak) so that I can boot from CD should the need arise.  ???

The grub rescue error message references a HDD I don't even have anymore!!  So, corrupt install?  System is working fine, except for full root dir and occasionally shutting off for no apparent reason!!

I was much happier before EFI!

---

### Post by Yellow Pasque on 2017-10-14
I don't see output of any commands, so you should check the link flocculant gave you.

>  occasionally shutting off for no apparent reason!!

Overheating can cause that. It seems odd to me that your CPU is at 60C on the EFI screen (with the fan screaming at ~3000RPM no less), unless you were doing something CPU intensive and took the screenshot after a quick reboot.

---

### Post by oldfred on 2017-10-14
If it is referring to a previous UUID, then you need to do a full uninstall/reinstall of grub.
Be sure to boot in UEFI mode and re-install grub-efi-amd64 for UEFI boot. Boot-Repair will walk you thru the full process  if in advanced mode you check the grub uninstall and full reinstall. I think they are on different tabs.

And then follow the instructions on housecleaning from drs305's thread, the link flocculant gave you

---

### Post by dkolars on 2018-01-02
Happy 2018... need to resurrect this thread... been working, traveling, sick, etc. so haven't been concentrating on this, but need to as I can't upgrade "things" with no room on the HDD...  even tho' there is room, just not accessible.

So, I attempted to reinstall UEFI boot from CD.  Got this message:


[ATTACH=CONFIG]278015[/ATTACH]

So, figured out how to boot from USB drive, did that, all seemed to work?

Re-booted, saw this:

[ATTACH=CONFIG]278016[/ATTACH]

So, I am still where I was.
 
Here's the view of HD1:

[ATTACH=CONFIG]278017[/ATTACH]

Installed Boot Info and got this:

[HR][/HR]                  ```
Boot Info Script 0.61      [1 April 2012]
============================= Boot Info Summary: ===============================
=> No boot loader is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 97 for .
 => No boot loader is installed in the MBR of /dev/sdf.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdg and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .
 => No boot loader is installed in the MBR of /dev/sdh.
 => No boot loader is installed in the MBR of /dev/sdi.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdj.
 => No boot loader is installed in the MBR of /dev/sdk.

sda1: __________________________________________________________________________
File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/ubuntu/fwupx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi

sda2: __________________________________________________________________________
File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________
File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________
File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdf1: __________________________________________________________________________
File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdg1: __________________________________________________________________________
File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdh1: __________________________________________________________________________
File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdi1: __________________________________________________________________________
File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdj1: __________________________________________________________________________
File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdk1: __________________________________________________________________________
File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc: ___________________________________________________________________________
File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================
Drive: sda _____________________________________________________________________
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sda1                   1   976,773,167   976,773,167  ee GPT

GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048     1,050,623     1,048,576 EFI System partition
/dev/sda2       1,050,624   943,421,439   942,370,816 Data partition (Linux)
/dev/sda3     943,421,440   976,771,071    33,349,632 Swap partition (Linux)

Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sdb1    *          2,048 3,907,028,991 3,907,026,944  83 Linux

Drive: sdf _____________________________________________________________________
Disk /dev/sdf: 3.7 TiB, 4000752599040 bytes, 7813969920 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sdf1                   1 4,294,967,295 4,294,967,295  ee GPT

GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdf1           2,048 4,592,742,399 4,592,740,352 Data partition (Linux)

Drive: sdg _____________________________________________________________________
Disk /dev/sdg: 1.4 TiB, 1500301910016 bytes, 2930277168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sdg1                  63 2,930,272,064 2,930,272,002  83 Linux

Drive: sdh _____________________________________________________________________
Disk /dev/sdh: 7.3 TiB, 8001563221504 bytes, 15628053167 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sdh1                   1 4,294,967,295 4,294,967,295  ee GPT

GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdh1           2,048 5,964,376,063 5,964,374,016 Data partition (Linux)

Drive: sdi _____________________________________________________________________
Disk /dev/sdi: 2.7 TiB, 3000592981504 bytes, 5860533167 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
Disklabel type: gpt

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sdi1                   1 4,294,967,295 4,294,967,295  ee GPT

GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdi1           2,048 2,639,307,661 2,639,305,614 Data partition (Linux)

Drive: sdj _____________________________________________________________________
Disk /dev/sdj: 1.4 TiB, 1500301910016 bytes, 2930277168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sdj1               2,048 2,930,276,351 2,930,274,304  83 Linux

Drive: sdk _____________________________________________________________________
Disk /dev/sdk: 1.4 TiB, 1500301910016 bytes, 2930277168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sdk1               2,048 2,930,277,167 2,930,275,120  83 Linux

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL
/dev/sda1        7F8C-92A2                              vfat       
/dev/sda2        bdd3e5be-fdc0-44e9-a9d2-4d7bfc44391c   ext4       
/dev/sda3        b5a3d266-0060-443c-964a-1858ae939a39   swap       
/dev/sdb1        cf1e9433-9424-4881-a8d3-60b14cf65089   ext4       HD2
/dev/sdc         a52cb84b-6e46-465a-842c-dc5a9dca0511   ext4       HD9
/dev/sdf1        dac3fdb7-5640-4f12-afa6-89e227b086de   ext4       HD8
/dev/sdg1        52ab9469-2cef-41e6-be93-4dfe830cc819   ext4       HD7
/dev/sdh1        6024ad6e-6480-4994-887a-ca4ee2e35642   ext4       HD4
/dev/sdi1        e2b492e0-e7f0-4b4a-98a6-fa969d46069f   ext4       HD3
/dev/sdj1        eceb9b86-289a-4af7-9575-94412d395ec4   ext4       HD6
/dev/sdk1        b5cfa05e-ebad-4241-a5f8-3213dd23a7e7   ext4       HD5

================================ Mount points: =================================
Device           Mount_Point              Type       Options
/dev/sda1        /boot/efi                vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sda2        /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)
/dev/sdb1        /media/HD2               ext4       (rw,nosuid,nodev,relatime,data=ordered)
/dev/sdc         /media/HD9               ext4       (rw,nosuid,nodev,relatime,data=ordered)
/dev/sdf1        /media/HD8               ext4       (rw,nosuid,nodev,relatime,data=ordered)
/dev/sdg1        /media/HD7               ext4       (rw,nosuid,nodev,relatime,data=ordered)
/dev/sdh1        /media/HD4               ext4       (rw,nosuid,nodev,relatime,data=ordered)
/dev/sdi1        /media/HD3               ext4       (rw,nosuid,nodev,relatime,stripe=8191,data=ordered)
/dev/sdj1        /media/HD6               ext4       (rw,nosuid,nodev,relatime,data=ordered)
/dev/sdk1        /media/HD5               ext4       (rw,nosuid,nodev,relatime,data=ordered)

=============================== sda2/etc/fstab: ================================
--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=bdd3e5be-fdc0-44e9-a9d2-4d7bfc44391c /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
#UUID=7F8C-92A2  /boot/efi       vfat    umask=0077      0       1
# swap was on /dev/sda3 during installation
UUID=b5a3d266-0060-443c-964a-1858ae939a39 none swap sw,x-gvfs-name=SWAP 0 0
#HD2
UUID=7F8C-92A2    /boot/efi    vfat    defaults    0    1

#Created using "Disks" - 9/2/17
LABEL=HD2 /media/HD2 auto nosuid,nodev,nofail,x-gvfs-show 0 0
LABEL=HD4 /media/HD4 auto nosuid,nodev,nofail,x-gvfs-show 0 0
LABEL=HD5 /media/HD5 auto nosuid,nodev,nofail,x-gvfs-show 0 0
LABEL=HD6 /media/HD6 auto nosuid,nodev,nofail,x-gvfs-show 0 0
LABEL=HD7 /media/HD7 auto nosuid,nodev,nofail,x-gvfs-show 0 0
LABEL=HD8 /media/HD8 auto nosuid,nodev,nofail,x-gvfs-show 0 0
LABEL=HD10 /media/HD10 auto nosuid,nodev,nofail,x-gvfs-show 0 0
LABEL=HD3 /media/HD3 auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=HD3 0 0
LABEL=HD9 /media/HD9 auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=HD9 0 0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================
GiB - GB             File                                 Fragment(s)

========= Devices which don't seem to have a corresponding hard drive: =========
sdd sde 

=============================== StdErr Messages: ===============================
cat: /tmp/BootInfo-Pqq1eiqY/Tmp_Log: No such file or directory
```
[HR][/HR]
So, I see other problems here, no drives associated with sdd or sde?  HD10 doesn't exist!  NO clue what's up with that.  Also note that even tho' I have formatted all disks/partitions to ext4, some are listed as "Linux" and some as "GPT".  Again, no clue why there is a difference.  Some are "Disklabel type: dos", some are Disklabel type: gpt".  NO clue what's up with those differences.

Thinking I need to scrub my / drive and start all over?  NOT enjoying this.

---

### Post by oldfred on 2018-01-02
Your attachments are not working, did you attach with paper clip icon in Forum's advanced editor?
And use code tags or # in advanced editor, if large text or terminal output to preseve formatting. 

Drives are either gpt(GUID) or MBR(msdos), UEFI and large disks use gpt, old drives (starting back 35 years ago) use MBR. If only Ubuntu or data you can use gpt on any drive, but Windows only boots in BIOS boot mode from a MBR partitioned drive and only in UEFI boot mode from gpt.
       MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

Drive order is set more by UEFI/BIOS than anything Else. And external drives may start at sdf and go up. Internal drives start as sda.
But all my systems have drives in port order. Originally I skipped some SATA ports and when plugging flash drive in, all my drives changed order. So if internal drives start at SATA0 or first port and use ports in order.

---

### Post by dkolars on 2018-01-03
Yes, used paper clip in Advanced, just edited and looks like they "took"?

Here's what I'm showing with df -Th:

```

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  7.8G     0  7.8G   0% /dev
tmpfs          tmpfs     1.6G  9.6M  1.6G   1% /run
/dev/sda2      ext4      443G  420G   87M 100% /
tmpfs          tmpfs     7.8G  168M  7.7G   3% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/sdc       ext4      3.6T  1.6T  1.9T  46% /media/HD9
/dev/sdb1      ext4      1.8T   40G  1.7T   3% /media/HD2
/dev/sdk1      ext4      1.4T  618G  688G  48% /media/HD5
/dev/sdg1      ext4      1.4T   45G  1.3T   4% /media/HD7
/dev/sdj1      ext4      1.4T  151M  1.3T   1% /media/HD6
/dev/sdi1      ext4      2.7T  1.6T  1.1T  60% /media/HD3
/dev/sdh1      ext4      7.3T  1.6T  5.4T  23% /media/HD4
/dev/sda1      vfat      511M  4.6M  507M   1% /boot/efi
/dev/sdf1      ext4      3.6T  1.6T  1.9T  46% /media/HD8
tmpfs          tmpfs     1.6G   56K  1.6G   1% /run/user/1000
```

So, even though sda2 is not anywhere NEAR that full, it says it is.  This prevents me from doing upgrades other than one at a time, then sometimes removing files to make room for the next upgrade, etc.

---

### Post by oldfred on 2018-01-03
Your drive is then a standard UEFI install with just the ESP - efi system partition, / (root) &  swap.

How you boot install media UEFI or Legacy/BIOS/CSM is then how it installs.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

But how you install may not be the default boot mode in your UEFI for your internal drive.
You should have 3 modes, UEFI Secure Boot, UEFI, and CSM. 
Many systems call Secure boot setting "Windows" or "Other", but fine print says if using Windows 7 use "Other" as Windows 7 does not support Secure boot.
And then you still have to chose UEFI or Legacy as default boot.

Some systems need a boot parameter to prevent runaway log files.

 Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[https://ubuntuforums.org/showthread.php?t=2327570](https://ubuntuforums.org/showthread.php?t=2327570) 

Check where data is, if not log file issue:

 # check sizes of 
Partition sizes
df -Th | grep sd| sort
Inodes:
 df -i
cd / or cd /home
sudo du -hc --max-depth=1
Shows just /
sudo du -hx --max-depth=1 / 2> /dev/null

I have not used autofs, so not familar with it, but it looks like it would be better for external drives. See post by TheFu for this users issues.
[https://ubuntuforums.org/showthread.php?t=2381567&p=13727038#post13727038](https://ubuntuforums.org/showthread.php?t=2381567&p=13727038#post13727038)

---

### Post by dkolars on 2018-01-03
Ran the commands you gave and get this:

```
dk@dk-desktop:/$ sudo du -hc --max-depth=1
[sudo] password for dk: 
du: cannot access './proc/5678/task/5678/fd/4': No such file or directory
du: cannot access './proc/5678/task/5678/fdinfo/4': No such file or directory
du: cannot access './proc/5678/fd/3': No such file or directory
du: cannot access './proc/5678/fdinfo/3': No such file or directory
0    ./proc
16K    ./mnt
14M    ./etc
132M    ./boot
13M    ./bin
4.5M    ./dev
4.1G    ./usr
4.0K    ./lib64
4.0K    ./srv
32K    ./snap
6.9T    ./media
du: cannot access './run/user/1000/gvfs': Permission denied
9.6M    ./run
13M    ./sbin
3.7M    ./tmp
4.0K    ./cdrom
611M    ./var
2.7G    ./home
497M    ./opt
683M    ./lib
19M    ./root
0    ./sys
6.9T    .
6.9T    total
```


```
dk@dk-desktop:/$ sudo du -hx --max-depth=1 / 2> /dev/null
16K    /mnt
14M    /etc
128M    /boot
13M    /bin
4.1G    /usr
4.0K    /lib64
4.0K    /srv
32K    /snap
8.0K    /media
13M    /sbin
3.7M    /tmp
4.0K    /cdrom
611M    /var
2.7G    /home
497M    /opt
683M    /lib
19M    /root
8.7G    /
```

Something is using 420 Gb, but it's certainly not showing up in any of the investigative results

```
dk@dk-desktop:/$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  9.6M  1.6G   1% /run
/dev/sda2       443G  420G   70M 100% /
tmpfs           7.8G  188M  7.7G   3% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/sdc        3.6T  1.6T  1.9T  46% /media/HD9
/dev/sdb1       1.8T   40G  1.7T   3% /media/HD2
/dev/sdk1       1.4T  618G  688G  48% /media/HD5
/dev/sdg1       1.4T   45G  1.3T   4% /media/HD7
/dev/sdj1       1.4T  151M  1.3T   1% /media/HD6
/dev/sdi1       2.7T  1.6T  1.1T  60% /media/HD3
/dev/sdh1       7.3T  1.6T  5.4T  23% /media/HD4
/dev/sda1       511M  4.6M  507M   1% /boot/efi
/dev/sdf1       3.6T  1.6T  1.9T  46% /media/HD8
tmpfs           1.6G   88K  1.6G   1% /run/user/1000

```

---

### Post by oldfred on 2018-01-03
This might be issue?
6.9T    ./media
8.7G    /

But that does not add up to 420GB?

Have you emptied trash and done housecleaning?

RecoverLostDiskSpace
 [https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

 Caution deborphan will delete anything you manually installed. See comment: 
 Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
[http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)

---

### Post by dkolars on 2018-01-04
I have tidied up everything I could think of to clean.  No change...  BUT, interesting thing happened, might be the problem?

I checked sizes with baobab & Krusader:

[ATTACH=CONFIG]278049[/ATTACH]   [ATTACH=CONFIG]278048[/ATTACH]

Then, I unmounted ALL the drives.  Then, I opened baobab and checked sizes of the / dir... WHOA...
[ATTACH=CONFIG]278050[/ATTACH]

ALL drives are unmounted... but, shows HD5 still active?  I can view contents with Krusader,, delete, move, etc., but nothing there (movies, videos, etc.) will play with only root directory active.  Weirdness!!

So, attempted to re-mount all... fail...
[ATTACH=CONFIG]278051[/ATTACH]  [ATTACH=CONFIG]278052[/ATTACH]

Needed to restart system, then got this...  oops, can't attach 6th pic...  reboot failed, had to power down to restart...

So, why would 441 Gb be seen by baobab in my root dir?  NOT viewable as "there" by any other program I've used...  Hmmm...

Oh, yes, when I attempted to mount drives via root mode Krusader, no matter **which** drive I right-clicked on, the error message said that HD4 could not be mounted.

---

### Post by oldfred on 2018-01-04
Do not know details with Krusader. But with Nautilus once you click on a partition it is remounted with defaults in /media/$USER.
But you cannot mount a partition twice and if mounted in fstab, it mounts to that path, which may not be same as default path.

With older Naulitus, I used to have two mounts in /media, both fstab and default, but only one  actually worked.
But now I mount everything like my data in /mnt/data. Then it does not show in Naulitus. But I link all folders into /home so I still see all the folders & files.

Do not mount drives by device like you have done. It will lead to confusion of which drive is which. Use UUIDs and better definitions for mount or use labels.
Drives may not have same device settings on reboot or if you replug drives in. When I add a flash drive my sdb becomes sdc on reboot and flash drive becomes sdb. I believe it is because I skipped a SATA port and then UEFI asssigns flash drive to hd1 which then is sdb.

       Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab) 
    
 Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well: 
   Typical fstab entry For ext4, copy & paste into fstab but use your UUID & mount point:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /mnt/data ext4 defaults,noatime 0 2 
   ** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data 
   ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
sudo nano /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a 

I stopped using gui tools to see drive usage, other than gparted. Some include my links or mounts, others do not. So your drive size may exceed your actual drive size as a program is also counting data from other mounts.

---

### Post by dkolars on 2018-01-04
In Krusader, right-click on drive name in list in <Media> brings up menu, "Mount" is one of the options.

I used to have them listed by UUID, but Disks changed it, & it worked, so I left it!!

Easily changed, so now looks like this:
```
UUID="cf1e9433-9424-4881-a8d3-60b14cf65089" /media/HD2 auto auto,user,rw 0 0
UUID="e2b492e0-e7f0-4b4a-98a6-fa969d46069f" /media/HD3 auto auto,user,rw 0 0
```

One of my forever gripes has been the fact that Linux does not mount the drives in the same order as the user labels them, so going to gparted and viewing the list will not tell you what drive is what without clicking on it... would love to see it be sdc=HD2, sdd=HD3, sde=HD4, etc.

> But now I mount everything like my data in /mnt/data. Then it does not  show in Naulitus. But I link all folders into /home so I still see all  the folders & files.

Not following you on this one.  I'm assuming that Nautilus is named something different in Xubuntu?  I have Files and File Manager (Thunar), but seldom use them. as Krusader does all I need and then some... double-pane file manager (I started with Norton Commander when it 1st came out = spoiled).  Why would mounting in /mnt be different or better than mounting in /media?

So, will re-boot, unmount all the extra drives, and see if HD5 still shows up in root...  Thanks!

---

### Post by oldfred on 2018-01-04
When I label partitions, and I try to always label them, gparted shows label.

With gpt drives there are now two labels.

```
lsblk -o NAME,LABEL,PARTLABEL,SIZE,UUID,MOUNTPOINT
NAME   LABEL   PARTLABEL    SIZE UUID                                 MOUNTPOINT
sda                       232.9G                                      
&#9500;&#9472;sda1 ESP     ESP         49.8G D966-440A                            /boot/efi
&#9500;&#9472;sda2 xenial  xenial      30.3G 5c1e1a3f-261f-4da5-a0c2-8f479b3039de /
&#9500;&#9472;sda3 ISO     ISO         20.5G ab916e15-8a74-4d6e-a0b1-32718a505dc7 
&#9492;&#9472;sda4         bionic      25.4G e1e5879e-1828-4a1c-806c-b29c426ccc34 
sdb                       931.5G                                      
&#9500;&#9472;sdb1 ESP_B   EFI System Partition
&#9474;                          48.9G F496-1330                            
&#9500;&#9472;sdb2 zesty   zesty       30.3G a9bd9a65-bc8c-41b1-95b1-2dceb66b2652 
&#9500;&#9472;sdb3 ISO_b   ISO_b       49.8G c395f36d-5e02-4913-a904-e336054b2eff 
&#9500;&#9472;sdb4 backup_b
&#9474;              backup_b    49.8G dd4e4a2e-4785-4441-91b0-28234b98e625 /mnt/backu
&#9500;&#9472;sdb5 server  server      30.3G b76dc590-99a3-4e34-af35-e0dd43507232 
&#9500;&#9472;sdb6 data    data       205.1G f9537995-8b44-4abb-b5fb-ec27023f57b2 /mnt/data
&#9500;&#9472;sdb7                      2.1G 3ef43e7c-8a35-4f8b-bc73-c91d6098d4cd [SWAP]
&#9500;&#9472;sdb8         yakkety     25.4G 6c042846-fc6c-4f5b-80fc-7aa678cf09b7 
&#9492;&#9472;sdb9 Fedora  Fedora      25.4G 5326d262-26af-4b38-a523-b0f4d261f1a4 
sdc                        57.7G                                      
&#9500;&#9472;sdc1 efi64   efi64      499.7M 1612-3F7C                            
&#9500;&#9472;sdc2 xenial64
&#9474;              xenial64    20.5G 602ee35c-eff1-4a18-b1e6-1912c3672f9a /media/fre
&#9492;&#9472;sdc3 data64  data        36.7G 4e00e71c-3c6d-4cd9-9051-63bc940eddef /media/fre

```

---

### Post by dkolars on 2018-01-05
Well, I believe it's fixed? :?:  Time will tell.

I unmounted all the external drives and the non-root internal, leaving only / mounted.  Ran baobab, and HD5 was still listed in the / drive, 241+ Gb...  So, disconnected HD5 from USB and power, and deleted HD5 from /.  Poof!!  9.1Gb in root, and drive no longer full!

So, backed up all my needed files/dirs and reformatted drive, re-installed 16.04.3, and it booted up fine.  Yay...  So, then, plugged the external hard drives in, mounted them, all seemed to be working fine.  Suddenly, <**crack**> from the HDD array.  A loud crack like a board splitting in Winter cold.  HD5 is now dead.  Stone cold dead. Hmmm...  Another project for later.  :guitar:I've got gigs coming up!!

(EDIT:  HD5 has a switch in external case... it tripped... working again... musta been all the excitement?)

But, main system is running well, again, and NO EFI... I have no idea why that ever showed up in the 1st place, but it's been nothing but trouble.  So I now have a logical boot order in the BIOS again:  CD, HDD, Floppy/USB.  

Another problem surfaced, as I added the lines for auto-mounting the external drives to the fstab file.  Then, system would not boot.  Got the <Ctrl-D> prompt.  So, booted from Live CD, removed those lines, and am now running smoothly again.  I'll mount them manually!  sheesh.

So, thanks for all your insights and assistance.  I retired as NT support 17 yrs ago, and at times like these, I still miss it!  Don't miss MS bs, however!!

Will mark this as "Solved".

---

