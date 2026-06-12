---
title: "partition hard drive in order to dual boot?"
date: 2018-08-28
forum: General Help
---

### Post by dannyk2 on 2018-08-28
Have just bought a 2TB Hard Drive and i would like to dual boot Ubuntu MATE 18.04 and openSUSE Leap 42.3 using GParted. It's been so long since i've done anything like this.
Could someone point me to an easy to follow tutorial please.

---

### Post by yancek on 2018-08-28
First thing is how new is the computer and does it use UEFI as the method is somewhat different.  Probably the first thing you need to decide is which you will use as primary and install it last as the default installation options will make the last one use its bootloader.  Create partitions you want for the first of sizes you want/need, then leave unallocated space to install the second and do the same.  Using GParted is explained at their site at the link below.  YOu can probably find other more detailed tutorials with an online search.

 [https://gparted.org/display-doc.php%3Fname%3Dhelp-manual](https://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

---

### Post by oldfred on 2018-08-28
If you never are going to install Windows in BIOS boot mode, I would suggest using gpt partitioning. You can boot in UEFI or BIOS when drive is gpt from Ubuntu. I would expect but do not know OpenSuse boot modes. Found this where user has UEFI/gpt.
[https://forums.opensuse.org/showthread.php/528400-Repair-a-broken-UEFI-GRUB2-openSUSE-boot-scenario](https://forums.opensuse.org/showthread.php/528400-Repair-a-broken-UEFI-GRUB2-openSUSE-boot-scenario)

I have multiple Ubuntu installs on both my SSD & HDD. And an ESP on both drives, but Ubuntu only allows/installs to first drive, usually sda. I did install Fedora & it allowed be to choose sdb's ESP and it then booted from sdb.

Do not know userid of OpenSuse. With Ubuntu I keep /home inside / (root) but have a large /mnt/data partition. That works across all my installs but that is only since first user is 1000, Fedora used be 500, but changed years ago to 1000. If wanting same data in multiple installs check user how it assigns user. Do not attempt to share /home.

Ubuntu now installs with just / (root) as default install. It will add an ESP if UEFI, or bios_grub if BIOS boot on gpt drive. It now uses a swap file, but will use a swap partition if one is found.

       Only if gpt -  all partitions in gpt are primary (no logicals):
    gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
    gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)

for gpt(GUID) or MBR(msdos) partitioning

Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]25-30+ GB Mountpoint / primary or logical beginning ext4 
[*]Etc 
[/LIST]

If using gparted, first thing to do is change from default MBR(msdos) partitioning to gpt(GUID).
      Select gpt under device, advanced over msdos(MBR) default partitioning before starting.
Or use gdisk which is in repository, now standard in newer installs: 

 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)

---

### Post by dannyk2 on 2018-08-29
Thanks for all the help and advice yancek and oldfred it is really appreciated.

---

