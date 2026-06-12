---
title: "Windows won't boot"
date: 2015-01-09
forum: General Help
---

### Post by elliot7 on 2015-01-09
Hi, so today I decided to procrastinate by trying to get Ubuntu to dual boot with my Windows 8.1 on my Sony VAIO Pro 13. I have tried to do it before but gave up as there are a bunch of issues with this particular laptop.

[http://lmgtfy.com/?q=sony+vaoi+pro+13+dual+boot+ubuntu](http://lmgtfy.com/?q=sony+vaoi+pro+13+dual+boot+ubuntu)

Anyway I installed Ubuntu to dual boot with Windows but only Windows would boot. After trying a few things, disablling/enabling secure boot, UEFI/legacy mode, turning of fast boot etc. I found this tutorial:

[http://steffankarger.nl/2013/12/10/ubuntu-13-10-on-the-sony-vaio-pro-13](http://steffankarger.nl/2013/12/10/ubuntu-13-10-on-the-sony-vaio-pro-13)

I'm pretty much completely new to linux so I started pasting in some of the commands into the terminal without properly reading the tutorial. 

I typed in this bit:
sudo mount /dev/sda1 /mnt

and then:

cd /mnt/EFI
sudo mkdir -p Microsoft/Boot
sudo cp ubuntu/* Microsoft/Boot/*
sudo cp Microsoft/Boot/shimx64.efi Microsoft/Boot/bootmgfw.efi
cd ~
sudo umount /mnt

Before actually installing ubuntu (while on the try before you install thingy). I had a few errors, it said it couldn't find "ubuntu". I can't remember the exact error.

Anyway, after this I realised I was still on the trial, running from the USB, so I went to install it properly. It got an error about something being mounted, and that I should try to unmount before installing. I clicked yes, but it later said it failed to install.

I tried to run Windows afterwards and now nothing will boot. Here's my boot repair log: [http://paste.ubuntu.com/9698996/](http://paste.ubuntu.com/9698996/)

I am really screwed! I have coursework due in on Monday and I can't access it! I'm feeling sick to my stomach :-|

I would really like to be able to undo the stuff I did to the bootfiles. I don't want to accidently do any more damage. I'm hoping someone can look at the boot repair info and tell me what to do.

Thank you,

Elliot

Edit: Here's what GParted looks like:

[IMG]http://i.imgur.com/0yYynhM.jpg[/IMG]

How ****ed am I? :'(

---

### Post by oldfred on 2015-01-09
You do not have Windows. 

You have only three partitions, the efi as sda1, sda2 that gparted cannot open for whatever reason and swap. But if you installed Ubuntu that would be a Linux partition with corruption. Windows has to have a NTFS partition.

Did you reinstall Ubuntu and not use Something Else. Auto reinstall will overwrite the entire hard drive. 

If you have data, you may be able to recover some, but not all as now Linux has overwritten part of it. STOP using sytem, only use live installer.

You may be able to restore NTFS partitions and then do a restore/reinstall if the installer sees a Windows install. Otherwise you have to totally reinstall. Your Product ID is only valid for your Sony version of Windows. Sony may offer the recover set of DVD for a nominal charge. If not you have to purchase a totally new copy of Windows or use Ubuntu.

       [URL="https://help.ubuntu.com/community/DataRecovery"]https://help.ubuntu.com/community/DataRecovery
[/URL]
 [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

The partitions need to look like this, not sure if Sony has a recovery first or last. There usually are two recover partitions, one Windows and one Sony, the efi partition, a system reserved and the main Windows install.
      
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

In this thread a Sony user posted from gparted, his partition structure so your may be similar.
[http://ubuntuforums.org/showthread.php?t=2227580](http://ubuntuforums.org/showthread.php?t=2227580) [URL="https://help.ubuntu.com/community/DataRecovery"]
[/URL]

---

### Post by elliot7 on 2015-01-09
Alright, thanks for all that info. I'm not quite sure what I did, but I definately want to recover some important documents and my Windows product key.

[http://i.imgur.com/UWFoTfn.png](http://i.imgur.com/UWFoTfn.png)
[http://i.imgur.com/hvU1zk2.png](http://i.imgur.com/hvU1zk2.png)

I'm going to try and recover [SSD]

---

### Post by oldfred on 2015-01-09
I would try to bring back all the NTFS & FAT32 partitions and none of the Linux partitions. Then see what you have. 
If you can do deeper search on your main install and recovery any data do that first.

You may not be able to recover a fully working system, but it may be repairable.

---

### Post by elliot7 on 2015-01-10
Hi fred, sorry to keep bugging you...

I've given up on recovery, I just want to install Windows 8.1 back on my laptop. I'm really struggling with this as I don't have a Windows PC to create a bootable live USB with something like WinUSB Maker. Is there some software for Ubuntu which I can use to create a bootable Windows USB? I have an ISO of Windows 8.1 downloaded to a separate HDD.

---

### Post by oldfred on 2015-01-10
I have seen multiple threads that then get very long on trying to create a Windows flash drive from Linux. Not sure if possible or not.

I did create a Windows 7 repair flash drive, but the only way I was able to do that was to create a DVD, and boot & use DVD to copy itself to the flash drive. There were some commands in Windows I ran, but do not now remember as I have not used Windows for a couple of years.

The product key you have is only for the vendor/OEM version of Windows you have. You have to contact vendor to get a new set of recovery DVDs.

 Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)

---

