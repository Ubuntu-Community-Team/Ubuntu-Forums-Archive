---
title: "can I put Windows XP on with Ubuntu already on?"
date: 2014-05-02
forum: General Help
---

### Post by lizpy66 on 2014-05-02
Like the title says I want to put Windows XP on my Ubuntu 14.04 laptop, it has UEFI if that matters, without having to delete and reinstall Ubuntu due to too many stuff. I have about. I have 77gb I left so that should be enough, I can delete more if I need to easily. If there's a way then PLEASE explain it in a step by step way as if you were explaining it to an idiot cause I realllly do not want to screw this up. Also I have flashdrives to back up important data so that won't be a problem and I only have one harddrive on my laptop, I mainly just want XP for gaming and Ipod support since I hate using the other old mac I have and even that's running out of space on it's 40gb HDD.

Thanks in advance

---

### Post by fkkroundabout on 2014-05-02
1. gparted - make your linux EXT partition smaller
2. make a new NTFS partition with what's left
3. instruct UEFI to boot from your windows disc
4. install windows to partition

alternatively: virtual machine or seperate hard drive

---

### Post by HermanAB on 2014-05-02
Rather install Virtualbox and install XP inside a virtual machine.  That gives you more control over this insecure disaster and it will actually run faster than natively too.

---

### Post by lizpy66 on 2014-05-02
Virtualbox doesn't run too well on my 4GB ram, 2.4ghz processor haha I tried it. I think I will try fukkroundabout's advice and will post back here if it works :) I will try it sometime this weekend, thanks for the advice :) very helpful though I'm concerned I won't know how to make the linux EXT smaller

---

### Post by Luke M on 2014-05-02
You need to determine how your disk is partitioned: MBR or GPT? Because XP only supports MBR.

---

### Post by lizpy66 on 2014-05-02
How would I figure this out? I don't know what those terms mean to be honest

---

### Post by monkeybrain20122 on 2014-05-02
Put it in virtualbox and cut off internet access. XP I.S. D.E.A.D. You don't make room for a dead OS, when is this XP necrophilia going to end? The sight of XP makes me physically sick. :)

---

### Post by lizpy66 on 2014-05-02
As I said earlier, Virtualbox doesn't run good on my laptop. It was sluggish and heated up my laptop past it's threshold at one point. X.P won't be getting updates but I most likely won't be using it for internet, just for games until I get money for a new computer then I'll put Windows 7 and Ubuntu on that.

---

### Post by oldfred on 2014-05-02
MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)


 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

But XP will not read gpt partitioned drives. Newer Windows will read gpt partitioned drives, but only boot from gpt drives with UEFI. 
Ubuntu will boot from gpt partitioned drive with either BIOS or UEFI.

---

### Post by lizpy66 on 2014-05-02
How would I check to find out if I have gpt or mbr?

---

### Post by oldfred on 2014-05-02
Run this:
```
fred@fred-Precise:~$ sudo parted -l
[sudo] password for fred: 
Model: ATA MAXTOR STM316081 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: [COLOR=#ff0000]msdos[/COLOR]

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  59.0GB  59.0GB  primary  ntfs         boot
 4      59.0GB  80.0GB  21.0GB  primary  fat32
 2      80.0GB  160GB   80.0GB  primary  ext3


Model: ATA MAXTOR STM316081 (scsi)
Disk /dev/sdb: 160GB
Sector size (logical/physical): 512B/512B
Partition Table:[COLOR=#ff0000] gpt[/COLOR]

Number  Start   End     Size    File system     Name      Flags
 1      17.4kB  8225kB  8208kB                            bios_grub
 2      8225kB  26.2GB  26.2GB  ext4            MAVERICK
 3      26.2GB  29.4GB  3142MB  linux-swap(v1)
 4      29.4GB  160GB   131GB   ext4

```

Not booting Maverick anymore from sdb.

---

### Post by lizpy66 on 2014-05-02
It says my partition table is loop..

---

### Post by JayKay3OOO on 2014-05-02
XP is 12 years old

Windows 7 is 4 years old

Windows 95 is 18 years old 

C'mon. We all miss Quake 2. That intro... :guitar:

---

### Post by oldfred on 2014-05-02
If partition is loop that sounds like wubi inside a NTFS partition. wubi only works on MBR partitions.

---

### Post by lizpy66 on 2014-05-02
oh so this might work still? yay, so how would I go about doing this? download gparted and make the leftover space into NTSF then install XP for that??

---

### Post by oldfred on 2014-05-02
Post this so we know your exact partitions:

sudo parted -l

---

### Post by lizpy66 on 2014-05-02
now it says gpt up top..but loop down further


Model: ATA WDC WD3200BPVT-6 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size   File system  Name  Flags
 1      1049kB  512MB  511MB  fat32              boot
 2      512MB   768MB  256MB  ext2
 3      768MB   320GB  319GB                     lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 3725MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  3725MB  3725MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 316GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  316GB  316GB  ext4


Error: /dev/zram0: unrecognised disk label                                

Error: /dev/zram1: unrecognised disk label

---

### Post by oldfred on 2014-05-02
I do not know about zram nor LVM.
But with LVM you cannot use standard partition tools, but must use LVM tools.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
2014_02_22_Preparing Logical Volumes For Ubuntu Installations
[http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html](http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)
sudo apt-get install lvm2
sudo vgchange -ay
LVM gui tool:
[http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/)
sudo apt-get install system-config-lvm

---

### Post by slooksterpsv on 2014-05-02
A few questions - what are the specs of your machine, do you have the make an model?

XP I would highly suggest using Windows 7 with XP Mode if you need to run classic apps or run in VirtualBox - you said it was slow, but if you install the guest additions and depending on the CPU it can be pretty quick (usually 80%+ near native speed with the Guest Additions).

If there's a specific reason you need XP, such as legacy software, we may be able to point you in a better direction such as WINE, DOSBOX, or alternative apps.

---

### Post by lizpy66 on 2014-05-03
Hp pavilion G6 with 4gb Ram, 3.3 usable. 1400Mhz processor, Radeon HD 7420G HD graphics card

Virtualbox just spikes my laptop as I've said before so it's pointless to do it and I'm using XP for games and ipod support.

I use WINE and DOSBOX but they don't work for everything.

---

### Post by monkeybrain20122 on 2014-05-03
If you have 4 gb of ram and you can't run xp smoothly you are setting it up wrong. :)

---

### Post by lizpy66 on 2014-05-03
how would I set about doing it?

Sorry for late replies, I have to re install Ubuntu 14.04 after unity panel service won't stop going at 50% CPU at mininum

---

### Post by slooksterpsv on 2014-05-04
Depending on the CPU (MHz means nothing anymore) it could be a few different things.

VirtualBox, if you have more than 2 CPUs (e.g. quad-core) I'd allocate 2 to XP, install guest additions, and enable 2D Acceleration - that works for me.

---

