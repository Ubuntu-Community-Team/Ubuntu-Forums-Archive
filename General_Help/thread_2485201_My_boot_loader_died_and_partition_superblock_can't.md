---
title: "My boot loader died and partition superblock can't be read"
date: 2023-03-22
forum: General Help
---

### Post by dougleclair on 2023-03-22
Hello Ubuntu gurus,

Running Ubuntu 20.04.5 LTS and my server was stuck this morning (I noticed an internal error on my NextCloud), upon restart it seems the boot loader is missing. The computer immediately boots to BIOS. The SSD drive shows up in BIOS.

If I use the Ubuntu Live USB I can see all of my data, but I am seeing some errors. I used Duplicity to dump what is accessible to my QNAP NAS.

I am not sure if it was a write error, bad update or a failing SSD (it's only a year old).

Any advice for getting my system back up and running out be appreciated!

I tried Boot-Repair but it could only generate the following report:

[https://paste.ubuntu.com/p/C4xkfc62xS/](https://paste.ubuntu.com/p/C4xkfc62xS/)

---

### Post by MAFoElffen on 2023-03-22
I suspect a filesystem error... From an Ubuntu LiveUSB, open a terminal session and do a good backup, if you can. Then do:
```

sudo mke2fs -n /dev/nvme0n1p2

```
With the -n flag it will not make any changes, say y for yes... Copy the number down in the last line. That is where the backup superblock should be located.

If it said there was a problem reading the first superblock, but was able to read the second on on the last line, then do

For example, let's say the number you copied down was "32768". This is an example. Please substitute that number with what you copied down.
```

sudo e2fsck -b 32768 /dev/nvme0n1p2

```
That will substitute the superblock with the backup superblock.

---

### Post by TheFu on 2023-03-22
Check the SMART data on the SSD (smartmontools is the package to install). Look for issues.  SSDs do fail.  A friend had a high quality SSD from THE name in SSDs fail within 2 weeks.  Got it replaced, no questions asked.  

Hopefully, your SSD is still within the warranty it SMART shows it is failing/failed.  Might want to lay down encryption to the working cells before returning, if they even ask for it back.

---

### Post by Bashing-om on 2023-03-22
Hello dougleclair - Welcome to the Forums :D


My plus 2 in addition to the ups !

In cases as this - I boot up a live USB and
1) run a fiie system check
```

sudo fdisk -lu ##to know what partitions are the targets of the checks
sudo fsck /dev/sda1 ##assuming that "sda1" is where your root (/) file system resides -- #separate partitions for /home and /var - check them too

```
2) run a health check on the drives - Run a short and long test--at different times. The long test could take several minutes.
```

sudo apt install smartmontools
sudo smartctl -t short /dev/sda
sudo smartctl -t long /dev/sda

```
To view the results:
```

sudo smartctl -a /dev/sda

```
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

If both test are joyful - we can then consider re-installing the boot code.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by MAFoElffen on 2023-03-22
> **Bashing-om said:**
> If both test are joyful - we can then consider re-installing the boot code.

Just saying... Note lines 22, 94 & 122:
```

nvme0n1p2: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/[COLOR=#ff0000]nvme0n1p2: can't read superblock on /dev/nvme0n1p2.[/COLOR]

fdisk -l (filtered): ___________________________________________________________

Disk nvme0n1: 1.84 TiB, 2000398934016 bytes, 3907029168 sectors
Disk identifier: 3E09C321-7200-4F1E-AC1E-DAD4CF4F8B95
            Start        End    Sectors  Size Type
nvme0n1p1    2048    1050623    1048576  512M EFI System
nvme0n1p2 1050624    3147775    2097152    1G Linux filesystem
[COLOR=#ff0000]nvme0n1p3 3147776 3907028991 3903881216  1.8T Linux filesystem[/COLOR]
Disk mapper/ubuntu--vg-ubuntu--lv: 1.84 TiB, 1998782988288 bytes, 3903873024 sectors
Disk sda: 28.93 GiB, 31042043904 bytes, 60628992 sectors
Disk identifier: 0x2cf4ba3a
      Boot   Start      End  Sectors  Size Id Type
sda1  *          0  5999871  5999872  2.9G  0 Empty
sda2       5271500  5279499     8000  3.9M ef EFI (FAT-12/16/32)
sda3       6000640 60628991 54628352 26.1G 83 Linux

blkid (filtered): ______________________________________________________________

NAME                      FSTYPE      UUID                                   PARTUUID                             LABEL                    PARTLABEL
sda                       iso9660     2021-08-19-11-03-38-00                                                      Ubuntu 20.04.3 LTS amd64 
&#9500;&#9472;sda1                    iso9660     2021-08-19-11-03-38-00                 2cf4ba3a-01                          Ubuntu 20.04.3 LTS amd64 
&#9500;&#9472;sda2                    vfat        54C5-9C6C                              2cf4ba3a-02                                                   
&#9492;&#9472;sda3                    ext4        9212555e-a307-4fbc-8058-3484318dfb2d   2cf4ba3a-03                          writable                 
nvme0n1                                                                                                                                    
&#9500;&#9472;nvme0n1p1               vfat        8DD4-17DF                              1b12e706-e9cb-4192-829c-a789cf487d46                          
&#9500;&#9472;[COLOR=#ff0000]nvme0n1p2               ext4        4085cc3a-2bb4-47f7-8b0d-f16f9a890988   4713f0fb-152f-406d-a0da-e5d239f8f5f3[/COLOR]                          
&#9492;&#9472;nvme0n1p3               LVM2_member tjIZA3-hJ7J-uZdN-CvnN-tUoU-IkrF-6dO9t2 ef537492-711c-4f44-8abe-d7f0da251b14                          
  &#9492;&#9472;ubuntu--vg-ubuntu--lv ext4        cff4acf1-e99b-4591-83bc-60618e071cba   

```
/dev/nvme0n1p2 looks to me like a separate 1025MB /boot partition... which if the ext4 filesystem there was repaired, then would be mountable, and would mount to / in lv /dev/mapper/ubuntu--vg-ubuntu--lv

---

### Post by Bashing-om on 2023-03-22
:(

Bashing-om admits of failure to fully engage brain.

-yukkie-

---

### Post by dougleclair on 2023-03-22
Bingo! Thank you for the smartmontools tip. Drive shows failing SMART and is in Read Only mode due to Available Spare being below threshold -- 0%.

What would be the best course of action to clone the data onto a new drive? I'll get this one RMAed for replacement.

---

### Post by Bashing-om on 2023-03-22
dougleclair - 

I often see ddrescue as the goto tool:
[https://www.gnu.org/software/ddrescue/manual/ddrescue_manual.html](https://www.gnu.org/software/ddrescue/manual/ddrescue_manual.html)

-my bit to try and help-

---

### Post by TheFu on 2023-03-23
Well, cloning probably isn't the best idea, but if that's your goal, then ddrescue **is** the tool for that.  If you can't mount the file system read-only, then you have little choice.  Or if you have good backups, like everyone needs, then you are already covered.

If you can mount the storage read-only, then I'd use a backup tool that captures owner, group, permissions, ACLs, and xattrs.  rsync can do this, if run as root with some extra options.  Or use rdiff-backup or one of the 20 other backup tools available that aren't using images.  Why clone 2TB when only 500MB is actual data?

The problem with cloning everything on a drive is that you get all the cruft that has long been removed.  Cloning gets blocks with and without data. It doesn't know the difference.

---

### Post by dougleclair on 2023-03-31
So quick follow up. I cloned the drive onto the same model SSD using DDRescue and supposedly it had 99.9% recovery. However the bootloader seems missing and grub will not load.

I tried boot-repair via Live Drive but it cannot auto fix it and generates the following info:

[https://paste.ubuntu.com/p/9cWygrVpVQ/](https://paste.ubuntu.com/p/9cWygrVpVQ/)

Any other advice would be gratefully appreciated.

---

### Post by TheFu on 2023-03-31
> **dougleclair said:**
> So quick follow up. I cloned the drive onto the same model SSD using DDRescue and supposedly it had 99.9% recovery. However the bootloader seems missing and grub will not load.

I tried boot-repair via Live Drive but it cannot auto fix it and generates the following info:

[https://paste.ubuntu.com/p/9cWygrVpVQ/](https://paste.ubuntu.com/p/9cWygrVpVQ/)

Any other advice would be gratefully appreciated.

Would be helpful to see the exact ddrescue command used.  People often get confused and point at the wrong device files.

---

