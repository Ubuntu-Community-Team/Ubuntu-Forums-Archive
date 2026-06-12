---
title: "I have 2 x 2TB hdd's how to find which one I am booting from. Please"
date: 2019-12-26
forum: General Help
---

### Post by jacko777 on 2019-12-26
Hello all, I have 2 HDD's both of them are 2TB.  I need to find which drive I am booting from so that I can make an exact image of the working drive.
Unfortunately, both are the same make .. Seagate.  Both appear to have the same number, as in disk type.  How then might I find which one is the boot disk, and which one is the image.?

If, as so often happens, I get a reply of "More information needed."  Please ask what further information you require to answer the problem.

I cannot see that any further information is currently required, but if you ask me to do a certain task I will be happy to include it in the next post.

---

### Post by QIII on 2019-12-26
There is a down and dirty way to tell ... 

But before we talk about that, please post the results of
```
lsblk
```
```
sudo blkid
```
```
df -h
```

and 

```
sudo  lshw -class disk
```

By the way, I usually use a bit of white adhesive tape or paper to jot down the labels/names of the disks so they can be seen easily when you open your case for just this sort of reason.

---

### Post by jacko777 on 2019-12-26
```

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop1    7:1    0    20K  1 loop /snap/liveforspeed/8
loop8    7:8    0    74M  1 loop /snap/wine-platform-3-stable/6
sdb      8:16   0 223.6G  0 disk 
&#9500;&#9472;sdb2   8:18   0     1K  0 part 
&#9500;&#9472;sdb5   8:21   0   975M  0 part [SWAP]
&#9492;&#9472;sdb1   8:17   0 222.6G  0 part /
loop6    7:6    0   2.7M  1 loop /snap/resourcehacker/77
loop4    7:4    0 215.2M  1 loop /snap/wine-platform-runtime/54
sr0     11:0    1     2K  0 rom  
loop2    7:2    0  22.4M  1 loop /snap/snapd/5643
loop0    7:0    0 903.2M  1 loop /snap/0ad/129
loop9    7:9    0 215.2M  1 loop /snap/wine-platform-runtime/62
sdc      8:32   0   1.8T  0 disk 
&#9500;&#9472;sdc2   8:34   0     1K  0 part 
&#9500;&#9472;sdc7   8:39   0 195.3G  0 part /mnt/260AF8CC04A3FE55
&#9500;&#9472;sdc5   8:37   0 195.3G  0 part 
&#9500;&#9472;sdc1   8:33   0   731M  0 part 
&#9500;&#9472;sdc8   8:40   0  46.6G  0 part 
&#9492;&#9472;sdc6   8:38   0 195.3G  0 part /mnt/0df1777b-958e-4308-86c0-e53737f484e8
loop7    7:7    0  44.2M  1 loop /snap/gtk-common-themes/1353
sda      8:0    0   1.8T  0 disk 
&#9500;&#9472;sda2   8:2    0   2.4M  0 part 
&#9492;&#9472;sda1   8:1    0   1.6G  0 part 
loop5    7:5    0  54.6M  1 loop /snap/core18/1288
loop3    7:3    0  54.6M  1 loop /snap/core18/1279
loop10   7:10   0  22.4M  1 loop /snap/snapd/5754
rod@rod:~$ 

```
```

rod@rod:~$ sudo blkid
[sudo] password for rod: 
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda1: UUID="2019-02-27-09-57-36-00" LABEL="Ubuntu 16.04.6 LTS amd64" TYPE="iso9660" PTUUID="6fee4eb0" PTTYPE="dos" PARTUUID="6fee4eb0-01"
/dev/sda2: SEC_TYPE="msdos" UUID="3E97-4D51" TYPE="vfat" PARTUUID="6fee4eb0-02"
/dev/sdb1: UUID="0be19fc0-9213-4055-9906-4498a7951494" TYPE="ext4" PARTUUID="4175c627-01"
/dev/sdb5: UUID="dd297bea-1770-482f-883e-48b4a058d5a8" TYPE="swap" PARTUUID="4175c627-05"
/dev/sdc1: UUID="9409f286-37d1-41e0-8d07-605c2f8f05cc" TYPE="ext2" PARTUUID="eb576daa-01"
/dev/sdc5: LABEL="/" UUID="f78810d0-06ff-4a0e-8cf1-08d4efc32081" TYPE="ext4" PARTUUID="eb576daa-05"
/dev/sdc6: LABEL="boot" UUID="0df1777b-958e-4308-86c0-e53737f484e8" TYPE="ext4" PARTUUID="eb576daa-06"
/dev/sdc7: UUID="260AF8CC04A3FE55" TYPE="ntfs" PARTUUID="eb576daa-07"
/dev/sdc8: UUID="6cfc74bc-f2cc-480b-a5ce-7772fc202bed" TYPE="ext4" PARTUUID="eb576daa-08"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
rod@rod:~$ 

```




```
rod@rod:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           785M  9.5M  776M   2% /run
/dev/sdb1       220G   91G  118G  44% /
tmpfs           3.9G   67M  3.8G   2% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/loop1      128K  128K     0 100% /snap/liveforspeed/8
/dev/loop0      904M  904M     0 100% /snap/0ad/129
/dev/loop2       23M   23M     0 100% /snap/snapd/5643
/dev/loop3       55M   55M     0 100% /snap/core18/1279
/dev/loop4      216M  216M     0 100% /snap/wine-platform-runtime/54
/dev/loop6      2.8M  2.8M     0 100% /snap/resourcehacker/77
/dev/loop7       45M   45M     0 100% /snap/gtk-common-themes/1353
/dev/loop5       55M   55M     0 100% /snap/core18/1288
/dev/loop8       74M   74M     0 100% /snap/wine-platform-3-stable/6
/dev/loop10      23M   23M     0 100% /snap/snapd/5754
/dev/loop9      216M  216M     0 100% /snap/wine-platform-runtime/62
/dev/sdc6       193G   60M  183G   1% /mnt/0df1777b-958e-4308-86c0-e53737f484e8
/dev/sdc7       196G   71M  196G   1% /mnt/260AF8CC04A3FE55
tmpfs           785M  104K  785M   1% /run/user/1000rod@rod:~$ sudo  lshw -class disk
  *-cdrom                 
       description: DVD-RAM writer
       product: CDDVDW SH-222BB
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: SB00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
  *-disk
       description: ATA Disk
       product: WDC WD20EZRZ-00Z
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sda
       version: 0A80
       serial: WD-WCC4M7VJLF5E
       size: 1863GiB (2TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=6fee4eb0
  *-disk
       description: ATA Disk
       product: WDC WDS240G2G0A-
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       version: 0000
       serial: 1851B0803093
       size: 223GiB (240GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=4175c627
  *-disk
       description: ATA Disk
       product: WDC WD20EZRZ-00Z
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sdc
       version: 0A80
       serial: WD-WCC4N0NFVCP2
       size: 1863GiB (2TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=eb576daa
rod@rod:~$ 

```

Seems I made a large mistake....The drives are Western Digital,  not Seagate.  sorry about that.  I wonder if you can tell by the info. I have replied with.?

rod@rod:~$ 
[/code]

---

### Post by jacko777 on 2019-12-26
By the way, the other ssd is also there but as it is small by comparison, I did not include it.
Also I will most certainly take your hint to mark the drives as /dev/sda  and /dev/sdc

Rod.

---

### Post by dragonfly41 on 2019-12-26
As an added note I recently purchased a Crucial 1TB SSD but instead of attempting to install it inside my Dell PC, which already is dual boot configured with limited internal bays, I invested in a [Startech Dual Bay docking station]("https://www.startech.com/uk/HDD/Docking/dual-sata-hdd-dock~SDOCK2U33V"). I also purchased a [Dock Station or container into which the SSD is placed]("https://www.icydock.com/goods.php?id=80") and this in turn plugged into the Startech docking station. Extra cabling provided with the Startech docking station will allow me in due course to interface to older IDE drives to harvest any old data. I used boot-repair to be able to boot into any of several drives. I have an older generation SATA container also connected in which Ubuntu 18.04 is currently running (as I write this). Conclusion:adding an external docking station offers a lot of flexibility and it comes with its own power source.  Here is one [YouTube presentation]("https://www.youtube.com/watch?v=feL4e-yhdX4") (one of many I found by searching around).

---

### Post by jacko777 on 2019-12-26
> **dragonfly41 said:**
> As an added note I recently purchased a Crucial 1TB SSD but instead of attempting to install it inside my Dell PC, which already is dual boot configured with limited internal bays, I invested in a Startech Dual Bay docking station. I also purchased a [Dock Station or container into which the SSD is placed]("https://www.icydock.com/goods.php?id=80") and this in turn plugged into the Startech docking station. Extra cabling provided with the Startech docking station will allow me in due course to interface to older IDE drives to harvest any old data. I used boot-repair to be able to boot into any of several drives. I have an older generation SATA container also connected in which Ubuntu 18.04 is currently running (as I write this). Conclusion:adding an external docking station offers a lot of flexibility and it comes with its own power source.  Here is one [YouTube presentation]("https://www.youtube.com/watch?v=feL4e-yhdX4") (one of many I found by searching around).

OK Dragonfly41, all noted.  Might hunt for one of those later on, (as funds allow).

Thank you for the advice.

Rod.

---

### Post by yancek on 2019-12-26
The output you posted shows that you have 3 drives, 2 are 1.8TB(sda and sdc) and 1 is 223GB.  sdc has 6 partitions while sda has only 2, big clue there.  The output you posted shows that the / (root of the filesystem) is on sdb1 and those commands won't tell you where the boot files are.  Could be on that drive or another.      

> /dev/sdb1       220G   91G  118G  44% /

All 3 of the drives are Legacy/msdos so you have an MBR on each and there is not way to tell with the commands abovee which drive has the MBR code pointing to your Ubuntu install.  One way to obtain that information by using boot repair from the link below and using ONLY the Create BootInfo Summary option and reviewing the output when it finishes.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by QIII on 2019-12-26
In general, unless you did something specifically to make it otherwise, your boot information will be where your / is, and that is on sdb.  That is not a foregone conclusion, but we can start there.  What is probably the case is that your OS is on sdb.

sdb will probably be on the second SATA header (SATA1).

I don't see the output of 

```
sudo  lshw -class disk
```

there.

But you already have information on the the serial numbers of the disks, so we probably don't need that.  Find the serial associated with sdb and we can make a fair guess that it is the one you want to be sure you are booting from.  The serial number will be on the factory label on the disk housing, so you can look for that.

To be sure that is the one (assuming your MBR is there), you can use the down and dirty method:  unplug the other drive.  If you still get to your OS, that is the one you are booting from.  Mark that one as the boot device.

"sda" and "sdb" are assigned by the OS based on the motherboard's POST information reported to the OS. -- the first detected (probably on SATA0, but that is not always certain) will be called sda.  Don't label one "sda" and the other "sdb", however.  That may not always be reported as sda, particularly if you move your disks around on the headers.  Use a more descriptive label, like "boot" or something.  You might even use the UUID, which will not change.  I name my drives -- like "Wotan" or "Thor".

---

### Post by jacko777 on 2019-12-26
I hope this helps in your attempt to get me sorted.  The "sdb" drive has ubuntu 18.04 and as stated, it is also smaller.  Unless the computer boots to that drive, and I am not that well up on Linux, then I simply ignored it.
Thank you for your help to date, I guess if I must open the box and delve into the bowels of the machine, then so be it....

code:
rod@rod:~$ sudo  lshw -class disk
[sudo] password for rod: 
  *-cdrom                 
       description: DVD-RAM writer
       product: CDDVDW SH-222BB
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: SB00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: ATA Disk
       product: WDC WD20EZRZ-00Z
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sda
       version: 0A80
       serial: WD-WCC4M7VJLF5E
       size: 1863GiB (2TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=6fee4eb0
  *-disk
       description: ATA Disk
       product: WDC WDS240G2G0A-
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       version: 0000
       serial: 1851B0803093
       size: 223GiB (240GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=4175c627
  *-disk
       description: ATA Disk
       product: WDC WD20EZRZ-00Z
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sdc
       version: 0A80
       serial: WD-WCC4N0NFVCP2
       size: 1863GiB (2TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=eb576daa
rod@rod:~$ 
/code.

---

### Post by yancek on 2019-12-26
> I guess if I must open the box and delve into the bowels of the machine, then so be it....


There is no need to do that.   If all you want is to determine which drive your Ubuntu OS is booting from, download and run boot repair as instructed on the page (link in post 7 above).  You should select the 2nd option explained on the page and download it using the ppa.  You should NOT try to make any repairs as there is nothing to repair.  You should select the Create BootInfo Summary option.  This will output information on boot files as well as other information and tell you which drive has the Grub code in the MBR for Ubuntu.  It should be at the very top of the page.  When you run boot repair, it will output a link which you can post here if you can't make that determination on your own.

---

### Post by jacko777 on 2019-12-27
[https://paste.ubuntu.com/](https://paste.ubuntu.com/)

This contains a heap of data (33 lines), hope you may find it useful.?

Thanks yancek,

Rod.

---

### Post by westie457 on 2019-12-27
The link you posted is incomplete.
Run the 'BootRepair' tool again for the report and please post the full link generated. It will have a string of letters and numbers at the end.

---

### Post by jacko777 on 2019-12-28
Hello yancek, did you get the information from #7 ?
It was quite large (33 pages).  I tried to send it as I saw it but the thing was too large, so I sent the url that I was asked to write down.
At a large guess, I think the drive "sdc" might be the boot drive, but as I'm not sure, I don't want to take the image from the wrong drive and ghost it to the other drive.

Rod.

---

### Post by yancek on 2019-12-28
The link you posted above in post 11 doesn't contain anything. You need to use the Create BootInfo Summary option and post the link you get when it finishes here as explained in post 12.

---

### Post by oldfred on 2019-12-28
While I like and know how to read Summary Report from boot repair and often prefer that, this will give your mount & serial number on one line.

lsblk -fo +label,model,serial

---

### Post by jacko777 on 2019-12-28
[http://paste.ubuntu.com/p/CJYG6WGYY4/](http://paste.ubuntu.com/p/CJYG6WGYY4/)
this is the new lot of letters and numbers for boor repair.
Hope this helps.

Rod.

---

### Post by jacko777 on 2019-12-28
Hello RedFred, find enclosed, the data from your suggestion, and thank you.
Rod


```
rod@rod:~$ lsblk -fo +label,model,serial 
NAME   FSTYPE  LABEL   UUID                                 MOUNTPOINT LABEL   MODEL   SERIAL
loop1  squashf                                              /snap/core                 
loop8  squashf                                              /snap/live                 
sdb    iso9660 Ubuntu 18.04.2 LTS amd64
&#9474;                      2019-02-10-00-27-34-00                          Ubuntu 18.04.2 LTS amd64
&#9474;                                                                              WDC WDS 1851B08
&#9500;&#9472;sdb2 iso9660 Ubuntu 18.04.2 LTS amd64
&#9474;                      2019-02-10-00-27-34-00                          Ubuntu 18.04.2 LTS amd64
&#9474;                                                                                      
&#9500;&#9472;sdb5 swap    Ubuntu 18.04.2 LTS amd64
&#9474;                      dd297bea-1770-482f-883e-48b4a058d5a8 [SWAP]     Ubuntu 18.04.2 LTS amd64
&#9474;                                                                                      
&#9492;&#9472;sdb1 ext4    Ubuntu 18.04.2 LTS amd64
                       0be19fc0-9213-4055-9906-4498a7951494 /          Ubuntu 18.04.2 LTS amd64
                                                                                       
loop6  squashf                                              /snap/wine                 
loop4  squashf                                              /snap/snap                 
sr0                                                                            CDDVDW  R8SN6GA
loop2  squashf                                              /snap/wine                 
loop0  squashf                                              /snap/snap                 
loop9  squashf                                              /snap/reso                 
sdc                                                                            WDC WD2 WD-WCC4
&#9500;&#9472;sdc2                                                                                 
&#9500;&#9472;sdc7 ntfs            260AF8CC04A3FE55                     /mnt/260AF                 
&#9500;&#9472;sdc5 ext4    /       f78810d0-06ff-4a0e-8cf1-08d4efc32081            /               
&#9500;&#9472;sdc1 ext2            9409f286-37d1-41e0-8d07-605c2f8f05cc                            
&#9500;&#9472;sdc8 ext4            6cfc74bc-f2cc-480b-a5ce-7772fc202bed                            
&#9492;&#9472;sdc6 ext4    boot    0df1777b-958e-4308-86c0-e53737f484e8 /mnt/0df17 boot            
loop7  squashf                                              /snap/core                 
sda    iso9660 Ubuntu 16.04.6 LTS amd64
&#9474;                      2019-02-27-09-57-36-00                          Ubuntu 16.04.6 LTS amd64
&#9474;                                                                              WDC WD2 WD-WCC4
&#9500;&#9472;sda2 vfat    Ubuntu 16.04.6 LTS amd64
&#9474;                      3E97-4D51                                       Ubuntu 16.04.6 LTS amd64
&#9474;                                                                                      
&#9492;&#9472;sda1 iso9660 Ubuntu 16.04.6 LTS amd64
                       2019-02-27-09-57-36-00                          Ubuntu 16.04.6 LTS amd64
                                                                                       
loop5  squashf                                              /snap/0ad/                 
loop3  squashf                                              /snap/gtk-                 
loop10 squashf                                              /snap/wine                 
rod@rod:~$
```

---

### Post by oldfred on 2019-12-28
It looks like you cut off the right part of the output that includes model & serial number.
But Boot-Repair shows it.

```

lrwxrwxrwx 1 root root  9 Dec 29 10:39 ata-WDC_WD20EZRZ-00Z5HB0_WD-WCC4M7VJLF5E -> ../../sda
lrwxrwxrwx 1 root root  9 Dec 29 10:39 ata-WDC_WD20EZRZ-00Z5HB0_WD-WCC4N0NFVCP2 -> ../../sdc
lrwxrwxrwx 1 root root  9 Dec 29 10:39 ata-WDC_WDS240G2G0A-00JH30_1851B0803093 -> ../../sdb 
    
```

But it looks like you installed the Ubuntu live installer to  sda as it shows the ISO.
>         File system:       iso9660 
    

Your fstab also has a lot of mounts by UUID. Better to assign a easy description to each partition so then you have a better idea than some very long UUID.

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

---

### Post by jacko777 on 2020-01-05
Hello all, I haven't given up yet so sorry for the delay.  As you might have heard we have some serious fires over here in Aus.
As a volunteer fire fighter I have been rather busy of late.
I'm closer to 80 than 70, but I still respond in any capacity I can.  Usually in communications or sometimes in logistics.

Enough of me.!

I will have a good read of the URL last listed and see if I can learn what needs to be learned.
Thank you for your patience with me on this problem, I'll get back to you when I have read it.

Rod.

---

### Post by yancek on 2020-01-05
Your boot repair output shows at the very top that the only drive with boot code in the MBR pointing to a functioning core.img file is on sdc.  The model and serial number are on line 199 of boot repair, also posted above by oldfred.

---

