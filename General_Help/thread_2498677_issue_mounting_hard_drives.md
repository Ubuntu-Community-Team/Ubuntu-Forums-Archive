---
title: "issue mounting hard drives"
date: 2024-06-23
forum: General Help
---

### Post by badperson on 2024-06-23
Ok, so I think this issue will actually be pretty simple, but unfortunately I need to give a quick account of the saga I went thru to get to this point. 

I had been dual booting win10/ubuntu 22.04 for quite awhile just doing the normal updates along the way. At some point I decided to upgrade to 24.04 and ran into a ton of problems which I naturally did not document and don't fully remember. Around the same time I also felt it was time to upgrade from win 10 to 11, I just had to allow TPM in bios which took like 3 seconds...I had put that off for more than a year because I didn't want to deal with that. 

I will definitely get into the habit of documenting stuff I do in the future, because between the failed ubuntu upgrade, the win 11 upgrade, I first fried my grub menu which meant I couldn't get into ubuntu, so I booted with an ubuntu install usb drive, and did the try ubuntu to get into the file system and poke around, and somehow when I rebooted I had my grub menu (still 22.04), but I had somehow broken my windows install and I couldn't get into windows at all. 

I was pretty busy so I used ubuntu only for a couple of weeks, and yesterday I made a bootable win 11 usb and a bootable ubuntu usb. I started by installing windows which went fine...and I then installed ubuntu which also went fine. BUT....when I tried to add my two additionaly non system data hard drives to /etc/fstab using [this guide]("https://help.ubuntu.com/community/InstallingANewHardDrive"), when I restarted selecting ubuntu, got the login screen, entered my password, and then it just hung on a blank grey screen. 

So...I used the ubuntu live usb, got into to the /etc/fstab file, removed my changes and tried to restart again. Once again the grub menu was gone. So I reinstalled ubuntu thinking it would give me a repair option, but I then had a new install of ubuntu on this really small partition, I tried a whole bunch of stuff, but today threw in the towel, reinstalled win11 wiping all the partitions on the system drive, I then re-installed ubuntu so I have win 11 and ubuntu 24.04 successfully installed, each taking up half of the 1TB system drive, leaving the two additional hard drives used for data storage which have several years of data stored on them. 

so....I now want to mount these hard drives under the dirs `/media/files` and `/media/storage`


In nautilus they currently appear as in this image:
[IMG]https://ubuntuforums.org/asset.php?fid=286986&uid=401044&d=1719161263[/IMG]


here is the fdisk info:

```
Disk /dev/sda: 3.64 TiB, 4000787030016 bytes, 7814037168 sectors
Disk model: WDC WD40EFZX-68A
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: A554347B-E166-4BF3-8CB4-937A59CD26BB

Device     Start        End    Sectors  Size Type
/dev/sda1     34      32767      32734   16M Microsoft reserved
/dev/sda2  32768 7814033407 7814000640  3.6T Microsoft basic data

Partition 1 does not start on physical sector boundary.


Disk /dev/sdb: 1.82 TiB, 2000398934016 bytes, 3907029168 sectors
Disk model: CT2000MX500SSD1 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: A0809040-AF32-4363-A624-A0B6E7C17A87

Device     Start        End    Sectors  Size Type
/dev/sdb1     34      32767      32734   16M Microsoft reserved
/dev/sdb2  32768 3907026943 3906994176  1.8T Microsoft basic data

```

and blkid:

```
/dev/sdb2: LABEL="New Volume" BLOCK_SIZE="512" UUID="5890A39990A37C5E" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="6fcc5836-3089-46c6-ac83-c039fe6af244"
/dev/sda2: LABEL="New Volume" BLOCK_SIZE="512" UUID="928E93B78E939279" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="376c4ca9-8a67-4a70-996b-9f5d6964d57d"



```
If I add the following lines to /etc/fstab, should it work properly? 

```

/dev/sda2    /media/storage   ext3    defaults     0        2
/dev/sdb2    /media/files   ext3    defaults     0        2

```


or should I use UUIDs as according to [this doc?]("https://help.ubuntu.com/community/UsingUUID") 
I'm mainly trying to avoid the situation where I hung on that grey screen now that I have the OSs installed properly...don't want to go thru that again. 

thanks!!
bp

---

### Post by Bashing-om on 2024-06-23
badperson' Ho Boy --
Have you got homework yet to do :)

Windows 11 is a whole new ball game: [https://www.elevenforum.com/t/find-file-system-of-drive-in-windows-11.19335/](https://www.elevenforum.com/t/find-file-system-of-drive-in-windows-11.19335/)

One must know what file system the storage drives use (Fatxx, NTFS, ReFS) - and it will not be ext4 (linux)
then ya gots to tell linux how to cope with the Windows file system.
Something along the lines of:
```

UUID=12102C02102CEB83 /media/windows ntfs-3g auto,users,permissions 0 0

```
where you will substitute your own UUID in place of the 12102C02102CEB83, and perhpas institute some finer controls.
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
[http://ubuntuforums.org/showthread.php?t=2139423](http://ubuntuforums.org/showthread.php?t=2139423)

Bottom line here is that Windows is not Linux :D

[INDENT]proprieties must be observed
[/INDENT]

---

