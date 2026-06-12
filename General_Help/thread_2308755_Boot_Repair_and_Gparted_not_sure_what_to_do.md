---
title: "Boot Repair and Gparted not sure what to do"
date: 2016-01-05
forum: General Help
---

### Post by gavin15 on 2016-01-05
Hi,

I've had a year or so of great experience as an Ubuntu 14.04 user, till yesterday, gulp.  Suddently my computer lost WI-FI network access and on reboot it would just keeps going to the bios.  laptop is ASUS X550C and have tried all recommendations of key combinations and restarts for Aptio Setup Utility.  It's not dual boot just ubuntu.

But I can boot by "a try ubuntu" USB drive, so proves parts are working and can also access the HDD so that means that is ok, so leads me now to try the boot.  This is the information from boot repair  [http://paste.ubuntu.com/14409633/](http://paste.ubuntu.com/14409633/)  when I use Gparted I can see 3 drives, my HDD has key next to it, but does not show any free space, so if I partition will I loose data?

screen shot of Gparted - [https://drive.google.com/file/d/0B3SIDbYIQxEUV0tEc0NNSktwSG8/view?usp=sharing](https://drive.google.com/file/d/0B3SIDbYIQxEUV0tEc0NNSktwSG8/view?usp=sharing)
 
The boot I recognise as my USB.  The Ext2 I don't know what is that?    

According to the boot repair details and my partitions, not sure to follow instructions which might not be relevant and if it's telling me anything regarding the HDD.  I was tempted to make a partition of Ext2 but not sure what I'm doing so don't want to make things worse.  

Appreciate any advice and step my step guidence.

---

### Post by Bucky Ball on 2016-01-05
*Thread moved to **General Help**.*

Welcome. Looks like you may be using LVM. That makes it tricky(er). That may explain why you can't see partitions that are supposed to be there. The top of you bootinfo tells us you don't have Ubuntu installed at all, but wouldn't believe that as you are using LVM. Any reason why (just curious)? Have you just recently fiddled with LVM or RAID setup and that has caused this issue?

The bottom of your bootinfo shows this:

```
(debug) reinstall grub2 place-in-MBR no-BIOS_boot (mapper/ubuntu--vg-root)
(debug) reinstall grub2 place-in-MBR no-BIOS_boot (mapper/ubuntu--vg-root)
=================== Repair blocked
GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.


=================== Suggested repair
The default repair of the Boot-Repair utility would purge (in order to fix packages enable-raid enable-lvm) and reinstall the grub2 of mapper/ubuntu--vg-root into the MBR of sda, using the following options:     kernel-purge
Additional repair would be performed: unhide-bootmenu-10s


=================== Blockers in case of suggested repair
GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.


=================== Advice in case of suggested repair
The boot of your PC is in EFI mode, but no EFI partition was detected. You may want to retry after creating a EFI partition (FAT32, 100MB~250MB, start of the disk, boot flag).
Do you want to continue?


=================== User settings
The settings chosen by the user will not act on the boot.
```

Is there *anything* you did that you can remember prior to this happening that may have caused this hiccup? Did you change anything in the BIOS (UEFI to BIOS mode or vice versa)?

EXT2 is old. Best to use EXT4, but wouldn't go there (not sure why you want to create a new partition before recovering what is probably already on there). I think your problem may involve RAID or LVM, neither of which I know anything about, but there are others who do and hopefully might join us soon ...

---

### Post by gavin15 on 2016-01-05
First time I've looked a the BIOS was when it didn't boot, so no changes.  Only thing I doing was trying to delete a sub cache folder directory far from the root, then as explained lost wi-fi and could not shut down with 'shut down' so powered off, when I turned it on went to the BIOS.  because the partition was created automatially when I installed ubuntu over windows 8 setup, I was not aware it was LVM type partition.  There is no RAID as far as I'm aware. 

Currently looking at new laptops that come with ubuntu, this one ASUS I have had to press CTRL + F1 , then power back on to get the Wi-Fi to work but not too much hassle, unless you shutdown and startup everyday.

---

### Post by oldfred on 2016-01-05
Your ext2 is the default with LVM installs as boot partition is small. Often too small as many users are not maintaining it and housecleaning old kernels. With LVM that must be regularly done.

Did you choose full drive encryption when you installed as that uses LVM.
You also show an ESP - efi system partition. But if Boot-Repair wants a bios_grub partition to install grub that would be a BIOS install, not a UEFI re-install. Once you start using UEFI, you need to always boot hard drive & flash drives in UEFI mode not BIOS/CSM/Legacy or whatever option it gives you.

Gparted only shows the physical partitions, not your actual LVM logical partition. You have to use LVM tools.
While this thread is on resizing it also shows the standard mount and then mentions you can do other things like an fsck which may be what you need.
       How to: Mount & Resize an Encrypted Partition (LUKS) also mount
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)
sudo apt-get update && sudo apt-get install lvm2 cryptsetup
How to Resize a LUKS Encrypted File System.
[http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724)

Once you have it mounted in Live installer, then run fsck to repair partition.
      
 sudo e2fsck -f /dev/mapper/xxxx
where xxx is your logical partition.

If you really do not need encryption, it is a lot easier to just use standard install.

---

### Post by gavin15 on 2016-01-05
>Your ext2 is the default with LVM installs as boot partition is small.  Often too small as many users are not maintaining it and housecleaning  old kernels. With LVM that must be regularly done.

Hi thanks Old Fred, that makes sense, as updates could not be installed as there was not enough space, maybe it's ideal to create a bigger partition if I instal in the future or maybe a pre-installed OS laptop would have it done properly one would have hoped ;) it's annoying having to houseclean all the time. 

>Did you choose full drive encryption when you installed as that uses LVM.

I don't remember it was 18 months ago,  I installed ubuntu because I'd had enough of windows 8 after a few hours. But as an open source developer it's been great for me.  

Will have a go at this, when I have a clear head tomorrow, as it's quite complex.  

Thanks!

---

### Post by gavin15 on 2016-01-06
I've tried the following, which is strange 
```
sudo cryptsetup -v luksDump /dev/sda3
response - 
Device /dev/sda3 is not a valid LUKS device.

```

Then tried accessing normally
```
ubuntu@ubuntu:~$ sudo e2fsck -f /dev/sda3
e2fsck 1.42.9 (4-Feb-2014)
/dev/sda3 is in use.
e2fsck: Cannot continue, aborting.

```

Now what do I do?  

Also if I manage to get to the partition which part should I increase the size of, the boot partition part is too small right, that's why it can't boot?

command - 'sudo lvdisplay' gives me the following  
```
 

  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/root
  LV Name                root
  VG Name                ubuntu-vg
  LV UUID                JOHx8Y-cQdA-evfZ-MGYR-Lw45-qfRX-6BgBZe
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2014-08-18 16:15:28 -0400
  LV Status              available
  # open                 0
  LV Size                922.88 GiB
  Current LE             236256
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/swap_1
  LV Name                swap_1
  VG Name                ubuntu-vg
  LV UUID                9Ng8uk-eawQ-mYsc-370s-5nlz-zfAy-YH7o3Z
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2014-08-18 16:15:29 -0400
  LV Status              available
  # open                 0
  LV Size                7.89 GiB
  Current LE             2019
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1


```

---

### Post by oldfred on 2016-01-06
With LVM you do not work on physical partitions normally. You have to work on your logical partitions.

So you would run fsck like this? I do not use LVM, and only have copied a few commands so do not know full procedures.
The process to change the /boot partition is quite involved. Better to develop regular housecleaning of /boot. To change size you have to change the logical partition. Shrink the LVM, shrink the physical partition, move the physical partition and then expand  the /boot physical partition. All is dangerous, so good backups required. If really thinking about it, probably easier just to reinstall and restore from backup anyway. And unless you have to have encryption, better to use standard install, not LVM.

And do not use fdisk on gpt partitioned drives. Use parted or gdisk. I believe fdisk will finally be updated to at least do some things with gpt in new version with 16.04 since gpt now on all UEFI systems.

You may need other commands also, and make sure partition is unmounted when running fsck:
       sudo pvdisplay
sudo lvdisplay
mount
sudo vgscan --mknodes
sudo vgchange -ay
sudo e2fsck -f  /dev/ubuntu-vg/root

---

