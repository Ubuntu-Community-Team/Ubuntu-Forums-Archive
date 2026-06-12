---
title: "grub rescue&gt; fail"
date: 2015-09-18
forum: General Help
---

### Post by nknwn on 2015-09-18
I upgraded from Ubuntu 12 to Ubuntu 14 on an external HDD and was impressed by the new OS's speed. However, there was an error on boot which I decided to investigate.
The error was exactly like this:
```
Error : file not found 
Error : file not found 
Error : file not found 

Press Any Key to Continue
```

So I followed the advice here: [https://askubuntu.com/questions/460908/error-while-booting-ubuntu-14-04](https://askubuntu.com/questions/460908/error-while-booting-ubuntu-14-04)
*Solution* Don't follow this solution:
```
sudo grub-install /dev/sdX

sudo update-grub

sudo reboot 
```

and this is when I ended up with grub rescue> on boot.
I followed the advice here: [http://unix.stackexchange.com/questions/148041/recovering-from-grub-rescue-crash](http://unix.stackexchange.com/questions/148041/recovering-from-grub-rescue-crash)

but the **boot rescue> ls** command only listed the windows partitions on the local hard drive not all the partitions on the external hard drive. After reading a few web pages and trying this and that I was unable to get past the [B]boot rescue> 

Currently I'm reinstalling Ubuntu from scratch.
[/B]

---

### Post by yancek on 2015-09-18
You mention windows installed of course on the internal drive but neglect to mention which version.  If it is 8 or newer and was pre-installed it is likely using UEFI.  Is it?
Do you intent to keep the windows on a separate drive and boot it separately from Ubuntu from the BIOS on boot?  You might post the output of:  sudo fdisk -l to clarify the drive/partition information.  If you had the MBR method, were you booting both systems from the Ubuntu Grub bootloader?

---

### Post by nknwn on 2015-09-18
I didn't think to try a different computer when I got stuck in grub rescue. !! :)
However the Ubuntu drive is self contained and boots from the BIOS when I press a few keys. (esc > f9 > arrow keys > return)

The Windows laptop I used - this one - is a Windows 8.1 - It was pre-installed with Windows 8.

Here is the output from [B]sudo parted -l


[/B]```

Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                               Flags
 1      1049kB  420MB   419MB   ntfs         Basic data partition            hidden, diag
 2      420MB   693MB   273MB   fat32        EFI system partition          boot
 3      693MB   827MB   134MB                Microsoft reserved partition  msftres
 4      827MB   976GB   975GB   ntfs         Basic data partition             msftdata
 5      976GB   976GB   472MB   ntfs                                                  hidden, diag
 6      976GB   1000GB  24.1GB  ntfs         Basic data partition            hidden, msftdata


Model: WD 1200BEV External (scsi)
Disk /dev/sdb: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  36.2GB  36.2GB  primary   ext4            boot
 3      36.2GB  112GB   75.5GB  primary   fat32
 2      112GB   120GB   8314MB  extended
 5      112GB   120GB   8314MB  logical   linux-swap(v1)

```

---

