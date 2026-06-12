---
title: "No MBR on USB Sandisk 128GB?"
date: 2017-07-24
forum: General Help
---

### Post by mtcs2 on 2017-07-24
Hello.

First: I checked for posts on this within reason.

Second: Not using dual boot with Windows / GRUB. Most posts are related to this

Third: After power outage, can't recognize thumbdrive as bootable.  Was working prior to this.

Fourth: Partition intact as another Xubuntu thumbdrive installation mounts and reads files ok.

I need the Sandisk 128 back up.  The 32 GB working one is too small. Was the original I created the 128GB from

Help? Not sure how to restore MBR. 

Mount point: GParted says mount point for partition is /media/... maybe this causes a problem...?

---

### Post by oldfred on 2017-07-24
Power failure often causes file corruption which fsck can often fix. But sometimes it can totally damage system. 

External drives default mount at /media/$USER/label
Where $USER is your sign on user name.
and label is how you have labeled your flash drive partition(s). If not labeled it may be by UUID and then harder to tell which partition is which.

Post this:
sudo parted -l

And from mount just the /media lines like this:
```
/dev/sdc3 on /media/fred/system type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
/dev/sdc4 on /media/fred/data type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)

```

---

### Post by mtcs2 on 2017-07-25
> gammaray@gammaray-HP-Compaq-dc7700p-Convertible-Minitower:~$ sudo parted -l
Model: SanDisk Cruzer Dial (scsi)
Disk /dev/sda: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system     Flags
 1      16.4kB  28.0GB  28.0GB  primary  ext3            boot
 2      28.0GB  32.0GB  4011MB  primary  linux-swap(v1)


Model: SanDisk Ultra (scsi)
Disk /dev/sdb: 124GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type     File system     Flags
 1      16.4kB  120GB  120GB   primary  ext3            boot
 2      120GB   124GB  4233MB  primary  linux-swap(v1)





> /dev/sdb1 on /media/gammaray/Sancruzer 120gb type ext3 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)



Please note I have tried a few things using disks and gparted but no harm seemed to come from it... yet.

---

### Post by oldfred on 2017-07-25
The now older ext3 is not as reliable as ext4.
I normally do not put swap on my full installs on flash drives as I have enough RAM that my normal use does not ever use swap. I also only now use gpt, even if BIOS boot as slightly more reliable with backup partition table. But gpt requires extra partitions.
Is drive an SSD or flash drive?

Back up partition table.
 Backup partition table structure to text file & save to another device.
sudo sfdisk -d /dev/sdb > PTsdb.txt 

      
 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by mtcs2 on 2017-07-25
For 128GB Looks like it shows MBR, primary and boot flags.

? :sad: ?

They are both usb flash drives

---

### Post by oldfred on 2017-07-25
Did you back up partition table on 128GB?
And run fsck?

---

### Post by mtcs2 on 2017-07-25
Please note the system does not see 128gb drive as bootable, if this makes any difference.

Not yet have to make new CD and going to work now...

To be continued...

---

### Post by oldfred on 2017-07-25
Grub does not use boot flag, but a few BIOS will only boot a system with a boot flag, so we still suggest one on a primary partition. 

If you had not mentioned power failure, my first suggestion would be to reinstall grub or run Boot-Repair's summary report to see what issue might be.
         Just run the summary report, the auto fix sometimes can create more issues.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by mtcs2 on 2017-07-25
Couldn't let go. Late to work. Used installed 32gb flash drive.

When unmounted 128gb it reverted from sdb to sda ...

> gammaray@gammaray-HP-Compaq-dc7700p-Convertible-Minitower:~$ sudo parted -l
Model: SanDisk Ultra (scsi)
Disk /dev/sda: 124GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type     File system     Flags
 1      16.4kB  120GB  120GB   primary  ext3            boot
 2      120GB   124GB  4233MB  primary  linux-swap(v1)


Model: SanDisk Cruzer Dial (scsi)
Disk /dev/sdb: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system     Flags
 1      16.4kB  28.0GB  28.0GB  primary  ext3            boot
 2      28.0GB  32.0GB  4011MB  primary  linux-swap(v1)


gammaray@gammaray-HP-Compaq-dc7700p-Convertible-Minitower:~$ 



> gammaray@gammaray-HP-Compaq-dc7700p-Convertible-Minitower:~$ sudo e2fsck -C0 -p -f -v /dev/sda1
                                                                               
      516541 inodes used (7.05%, out of 7323648)
       24148 non-contiguous files (4.7%)
         433 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 22500/595/0
    17623888 blocks used (60.16%, out of 29293308)
           0 bad blocks
           8 large files

      388033 regular files
       71343 directories
          55 character device files
          25 block device files
           0 fifos
          15 links
       57050 symbolic links (50137 fast symbolic links)
          26 sockets
------------
      516547 files
gammaray@gammaray-HP-Compaq-dc7700p-Convertible-Minitower:~$ 



---

### Post by oldfred on 2017-07-25
The fsck I posted is a two step process.
First part only runs the parts that do not require an answer if an error appears.
Second part just auto responds with yes if there is an error.

So also run the second part and then see if you can mount it and see data.
Then see if bootable.

---

### Post by Kris_M on 2017-07-26
Whenever I have a USB flash drive that has no partition table on it I just boot to GPARTED on a thumb drive, and also have the offending drive plugged in, delete whatever may be on it, create an MBR (or whatever is your choice), and then create a full drive partition as FAT32 (or whatever your preference).

---

### Post by mtcs2 on 2017-07-28
Ok. second part e2fsck...

Still does not boot... maybe disk identifier changed from HD back to Removable?

> gammaray@gammaray-HP-Compaq-dc7700p-Convertible-Minitower:~$ sudo e2fsck -f -y -v /dev/sda1
e2fsck 1.42.13 (17-May-2015)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

      516573 inodes used (7.05%, out of 7323648)
       24150 non-contiguous files (4.7%)
         433 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 22502/595/0
    17623973 blocks used (60.16%, out of 29293308)
           0 bad blocks
           8 large files

      388052 regular files
       71356 directories
          55 character device files
          25 block device files
           0 fifos
          15 links
       57050 symbolic links (50137 fast symbolic links)
          26 sockets
------------
      516579 files
gammaray@gammaray-HP-Compaq-dc7700p-Convertible-Minitower:~$ 



---

### Post by mtcs2 on 2017-07-28
Does this give Bootrepair URL?

Did not know this install used GRUB probably for USB boot?


Here it is...[http://paste.ubuntu.com/25190544/](http://paste.ubuntu.com/25190544/)


> Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 
    30034728 of the same hard drive for core.img. core.img is at this location 
    and looks for (,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------
 => Grub2 (v1.99-2.00) is installed in the MBR of /dev/sdb and looks at sector 
    49555784 of the same hard drive for core.img, but core.img can not be 
    found at this location.


---

### Post by mtcs2 on 2017-07-28
> **Kris_M said:**
> Whenever I have a USB flash drive that has no partition table on it I just boot to GPARTED on a thumb drive, and also have the offending drive plugged in, delete whatever may be on it, create an MBR (or whatever is your choice), and then create a full drive partition as FAT32 (or whatever your preference).

Not helpful. Especially since I want to use what is on it.

---

### Post by oldfred on 2017-07-28
With MBR core.img is normally between first sector of drive & first sector of first partition. 
If gpt you have to have a bios_grub partition for core.img as there is not space after gpt's protective MBR in gpt formatted drives.

But both your drives look for core.img in install?  Perhaps they changed?

But if not found you need to reinstall grub. Not just install boot loader to MBR.

Use Boot-Repair's advanced mode and choose the full uninstall/reinstall option.

---

### Post by mtcs2 on 2017-07-28
> But both your drives look for core.img in install?  Perhaps they changed?

One 128gb was CloneZilla of the other 32gb

Remembering,  I think Windows 7 happened... something with bitlocker?

> 

But if not found you need to reinstall grub. Not just install boot loader to MBR.

Will give it a try.

---

### Post by mtcs2 on 2017-07-29
Currently:

sba1 is 32gb usb
sba1 is 128gb usb

Boot Repair :

1. Asked me if my USB is a removable drive...

2. Only let me select OS to boot sda1 / Tells me to use live CD to pick sdb1

3. After  Selecting sdb for installation of GRUB program wanted to delete GRUB on sda

I tried to back out of changes. I am not sure if I was successful.

[ATTACH=CONFIG]276169[/ATTACH]

now mount point for sdb1 is in boot-sav...

??? Trying reboot and remount

---

### Post by oldfred on 2017-07-29
If doing an UEFI install to a USB drive, there is no way currently to install grub to the USB external drive.
Best to backup up ESP on sda first, but you can easily reinstall the grub from an install on your internal drive.

And then you let grub install to the ESP on sda. You then have to manually copy /EFI/ubuntu folder from ESP on sda to ESP on external drive. 
Then copy again, but to /EFI/Boot on ESP on external drive and rename shimx64.efi to bootx64.efi.
And then in fstab on external drive change the UUID from the ESP on sda to ESP on external drive.

Its really a combination of grub, and UEFI. Grub only installs to sda, whether internal or external drive. But UEFI only boots from /EFI/Boot/bootx64.efi on external drives and that same path is often the fallback or hard drive boot entry for internal drives.

Some details in link in my signature and these:
[https://askubuntu.com/questions/906857/installing-ubuntu-on-usb-and-booting-from-destop-with-uefi](https://askubuntu.com/questions/906857/installing-ubuntu-on-usb-and-booting-from-destop-with-uefi)
[https://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi](https://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi)
 UEFI Full install to external USB drive or flash drive
[https://ubuntuforums.org/showthread.php?t=2338836](https://ubuntuforums.org/showthread.php?t=2338836) by Halbarad

---

### Post by mtcs2 on 2017-07-29
Using 32 bit computer...I don't believe it uses the new UEFI bios.

What is ESP?

---

### Post by oldfred on 2017-07-29
ESP is only for newer UEFI systems. It is the ESP - efi system partition and is FAT32 formatted.

If you are installing in BIOS boot mode on a gpt partitioned drive, you do have to have a bios_grub partition. It is 1 or 2MB unformatted with bios_grub flag. It can be anywhere on drive, so pick a larger partition and shrink by 2 MB and make a new unformatted 1MB bios_grub partition. Then grub should correctly install.

I have used gpt for partitioning since about 2010 and then all my systems were BIOS, so needed the bios_grub partition.

[https://help.ubuntu.com/community/DiskSpace#BIOS-Boot_or_EFI_partition_.28required_on_GPT_disks.29](https://help.ubuntu.com/community/DiskSpace#BIOS-Boot_or_EFI_partition_.28required_on_GPT_disks.29)

---

