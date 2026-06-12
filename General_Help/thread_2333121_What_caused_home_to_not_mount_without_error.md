---
title: "What caused /home to not mount without error"
date: 2016-08-07
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2016-08-07
i booted my 16.04 laptop this morning
that is odd no custom face icon
anyway i login a few times thinking i typed it wrong
guess my .Xauthority file needs deleting
login via tty
odd my name i not green like my .bashrc should make it
run ls command
wait i am in the root directory not my home one
whatever ls /home/me
permission denied
so i ls -l /home
root owns my folder i can fix that with chown
wait lets sudo ls -l my home folder
empty what the :confused:
sudo parted -l shows everything
sudo mount -a
ls /home/me
everything is there now
logout go back to the gui login
login everything is fine

why was there no error during boot like wait for home, press m or s?
the hdd with /home has no SMART errors 
* i have a SSD and a HDD installed on this laptop (traded the DVD drive for a ssd)

dmesg output:
[http://pastebin.com/m44A607e](http://pastebin.com/m44A607e)

---

### Post by oldfred on 2016-08-07
Is system older?
I would run fsck on all ext4 partitions and check Smart Status on drive(s).

I might worry about drive not mounting correctly on boot and then not seeing /home.
Is /home in a separate partition? So system might boot, but not immediately mount /home? May just need fsck. You show huge jumpor slow mounting of sda3 & even worse on sda2.
```
 [    8.289628] Bluetooth: RFCOMM ver 1.11
[   12.261445] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[  286.126694] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null) 


```

I also see a lot of ACPI warnings. Do you use or need a boot parameter for ACPI?
Have you tried one of these like adding nomodeset when booting?
       # Other settings in addition to nomodeset for other hardware related issues
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic

---

### Post by pqwoerituytrueiwoq on 2016-08-07
sda2 was mounted when i ran [FONT=courier new]mount -a[/FONT] manually
sda3 is mounted by my /etc/rc.local script
```
Model: ATA WDC WD3200BEKT-0 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name  Flags
 1      17.4kB  5371MB  5371MB  ext4                  msftdata
 2      5371MB  286GB   280GB   ext4                  msftdata
 3      307GB   309GB   2147MB  ext4                  msftdata
 4      309GB   320GB   10.7GB  linux-swap(v1)


Model: ATA MKNSSDCR60GB-DX (scsi)
Disk /dev/sdb: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  60.0GB  60.0GB  primary  ext4         boot
```
i thought fsck auto checked like every 20 mounts or so
i checked the last time it was done it was back in 2013* HDD is older than the laptop (7200rpm 320GB > 5200rpm 250GB)
checked out without error no smart errors

There was a time i needed acpi_osi='!Windows 1012'
 - [https://bugzilla.kernel.org/show_bug.cgi?id=55161](https://bugzilla.kernel.org/show_bug.cgi?id=55161)

---

### Post by oldfred on 2016-08-07
With ext4, I think the system relies on internal info if drive has issues. And then the fsck is just checking what drive has said. I still might try a full fsck.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by pqwoerituytrueiwoq on 2016-08-13
/dev/sdb1 is root
```
xubuntu@xubuntu:~$ sudo parted -l
Model: ATA WDC WD3200BEKT-0 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name      Flags
 1      17.4kB  5371MB  5371MB  ext4            Var       msftdata
 2      5371MB  286GB   280GB   ext4            Home      msftdata
 3      307GB   309GB   2147MB  ext4            Archives  msftdata
 4      309GB   320GB   10.7GB  linux-swap(v1)


Model: ATA MKNSSDCR60GB-DX (scsi)
Disk /dev/sdb: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  60.0GB  60.0GB  primary  ext4         boot


Model: iT1327 USB Flash Disk (scsi)
Disk /dev/sdc: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  32.0GB  32.0GB  primary  fat32        boot


xubuntu@xubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda2
                                                                               
       50469 inodes used (0.29%, out of 17113088)
         761 non-contiguous files (1.5%)
          21 non-contiguous directories (0.0%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 50200/212/2
    20733839 blocks used (30.29%, out of 68442924)
           0 bad blocks
           4 large files

       46732 regular files
        3679 directories
           0 character device files
           0 block device files
           0 fifos
           0 links
          48 symbolic links (46 fast symbolic links)
           1 socket
------------
       50460 files
xubuntu@xubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sdb1
                                                                               
      326728 inodes used (8.90%, out of 3670016)
          50 non-contiguous files (0.0%)
         685 non-contiguous directories (0.2%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 277845/101
     2156758 blocks used (14.72%, out of 14653320)
           0 bad blocks
           1 large file

      238798 regular files
       33260 directories
          57 character device files
          25 block device files
           0 fifos
          30 links
       54579 symbolic links (48692 fast symbolic links)
           0 sockets
------------
      326749 files
xubuntu@xubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda1
                                                                               
       14385 inodes used (4.39%, out of 328000)
          60 non-contiguous files (0.4%)
           7 non-contiguous directories (0.0%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 14126/24
      221584 blocks used (16.90%, out of 1311301)
           0 bad blocks
           1 large file

       13688 regular files
         443 directories
           0 character device files
           0 block device files
           0 fifos
           0 links
         245 symbolic links (227 fast symbolic links)
           0 sockets
------------
       14376 files
xubuntu@xubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda3
/lost+found not found.  CREATED.                                                         
                                                                               
         184 inodes used (0.14%, out of 131072)
           4 non-contiguous files (2.2%)
           1 non-contiguous directory (0.5%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 175
       93451 blocks used (17.83%, out of 524120)
           0 bad blocks
           1 large file

         172 regular files
           2 directories
           0 character device files
           0 block device files
           0 fifos
           0 links
           0 symbolic links (0 fast symbolic links)
           0 sockets
------------
         174 files
xubuntu@xubuntu:~$


```

---

### Post by oldfred on 2016-08-13
I see gpt partitioned sda.
But grub does not correctly install to gpt drive's protective MBR unless you have a 1 or 2MB unformatted partition with the bios_grub flag.
If your system works, you must have installed grub to sdb? And use sdb to boot?

I converted to all new drives as gpt years ago. But added bios_grub as first partition. Then when I thought I might convert to UEFI added both ESP - efi system partition and bios_grub as first partitions on every gpt drive. Even my large 32 or 64GB flash drives.

---

### Post by pqwoerituytrueiwoq on 2016-08-13
yes, sdb is the default boot device
normally i would make the main boot device sda by moving the drives in the system, but i figure the HDD bay would have better ventilation than some 2.5" cheap dvd caddy adapter
i have a 60GB ssd in the caddy adapter
it happened again today i got saw some notices during boot
```
[    4.129247] systemd[1]: root.mount: Found dependency on home.mount/start
[    4.129261] systemd[1]: root.mount: Breaking ordering cycle by deleting job home.mount/start
[    4.129264] systemd[1]: home.mount: Job home.mount/start deleted to break ordering cycle starting with root.mount/start
```
full dmesg: [http://pastebin.com/ZTU68hxw](http://pastebin.com/ZTU68hxw)
* i logged into hte tty and ran sudo mount -a at about 50 seconds after power on
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=5fbb664c-3d07-4801-b4e6-5a1ba1e01b93 /               ext4    errors=remount-ro,noatime,discard  0       1
# /home was on /dev/sda2 during installation
UUID=98ef1e15-845e-4f01-b28a-8c8e00629b9b /home           ext4    defaults        0       2
# /var was on /dev/sda1 during installation
UUID=b8dfd4b4-a155-4932-9629-cfa5630891a4 /var            ext4    defaults        0       2
# /var/cache/apt/archives was on /dev/sda3 during installation
#UUID=9b0788c7-d6e9-4db2-84e1-53400beb745b /var/cache/apt/archives ext4    defaults        0       2
# swap was on /dev/sda4 during installation
UUID=a89bd850-d2e1-4486-b3e6-40b04fccb9c3 none            swap    sw              0       0
# Move /tmp to ram to extenxd SSD Life
tmpfs                                     /tmp            tmpfs   defaults,noatime,mode=1777  0    0
# Move /media to ram to prevent clutter 
tmpfs                                     /media          tmpfs   defaults,size=1M,mode=755  0    0
# Move Root to /home to get it off the SSD
/home/root                                /root           bind    defaults,bind   0        0
```

---

### Post by oldfred on 2016-08-13
Why are you moving /root to /home?
It is rarely used as it is /home for /, and then mostly when running a gui app in root which normally you should not be doing anyway.

And SSD have life compatible to HDD. I do change a few settings to reduce writes, and leave some space, but otherwise do not worry about SSD.

---

### Post by pqwoerituytrueiwoq on 2016-08-14
paranoid 
id really like to know why systemd is not mounting everything in fstab

---

### Post by oldfred on 2016-08-14
It could be the ownership & permissions of /root?

I know when trying to houseclean files in /root even sudo often does not work. It has some other settings and I temporarily had to change ownership or permissions to houseclean and then change back.

---

### Post by pqwoerituytrueiwoq on 2016-08-14
/root unmounted is just a folder with normal permissions, once it is mounted to /home/root only root can access /root
it almost seems as if systemd does not mount fstab mount points in order and selects them in a random order
never had a issue with upstart screwing this up

---

