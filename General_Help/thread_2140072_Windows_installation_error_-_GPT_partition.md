---
title: "Windows installation error - GPT partition"
date: 2013-04-28
forum: General Help
---

### Post by malikge on 2013-04-28
Hi,
I am using Ubuntu-12.04 - 64 bit on my Lenovo G580 i5 laptop.


I have googled how to install window 7 after installing ubuntu and found out couple of good posts.
I have re-sized my partition table and made space for window 7 (Screenshot attached).


But when I try to install window7 (both 64 bit and 32 bit) it gives an error that:
> Windows cannot be installed on this disk. The selected disk is of the GPT partition style


I have searched and found out about UEFI and GTP stuff (which is beyond my understanding), and found out that either I have to use Gparted and create new Partition table or have to format my hard drive.


I don't want to mess up my ubuntu installation, because I have very important data and settings on it.


The output of:
```

razor@lenovoG580:~$ sudo parted /dev/sda unit s print
[sudo] password for razor: 
Model: ATA ST500LT012-9WS14 (scsi)
Disk /dev/sda: 976773168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt


Number  Start       End         Size        File system     Name  Flags
 1      194560s     792428543s  792233984s  ext4                  boot
 2      960200704s  976771071s  16570368s   linux-swap(v1)



```


I want to know is it possible for me to install windows 7 on 80Gb unallocated space without affecting my ubuntu installation?


Thanks

---

### Post by oldfred on 2013-04-28
You have to boot Windows in UEFI mode to install on a gpt drive as it only boots from gpt drives with UEFI.

Or you have to totally convert drive to MBR which theorically can be done  and reinstall grub, but I have not tried it.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)


  You cannot use the Win7 DVD in UEFI mode, you need to use BIOS mode or modify to USB with UEFI.
Convert Windows USB flash install to UEFI boot
[http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/](http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/)
Install Windows efi to new drive.
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

---

### Post by ronnyroll on 2013-04-28
it would be best to check with 
[http://en.wikipedia.org/wiki/Microso...rved_Partition](http://en.wikipedia.org/wiki/Microso...rved_Partition)
for better understanding

---

### Post by malikge on 2013-05-04
Hi, Oldfred I have not done this type of work before, so I am kinda little confuse here.

From your reply what I understood, is either I have to convert my hard drive to MBR or have to make boot-able USB with UEFI.

> [COLOR=#000000]Convert Windows USB flash install to UEFI boot[/COLOR]
[http://jake.io/b/2011/installing-win...x220-from-usb/]("http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/")
The link you have provided did not open.

> [COLOR=#000000]Or you have to totally convert drive to MBR which theorically can be done and reinstall grub, but I have not tried it.[/COLOR]

And for this option, I want to know does this will [COLOR=#000000]affect my ubuntu installation? Other than re-installing grub.

Thanks[/COLOR]

---

### Post by oldfred on 2013-05-04
It looks like that link is broken.
Try this, but I have not converted a Windows install to flash, but have just installed a Windows repair to flash drive.
 [https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB](https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB)

I have not converted to MBR. Actually now all new drives I only use gpt. It is newer and does not have to old 4 primary partition limit. It does have a limit of 128 partitions but I have not bumped into that. :)

UEFI is new and not as well understood, but with Windows 7 you will not have the secure boot issues that many are having with Windows 8 pre-installed systems. 

Either way best to make sure UEFI/BIOS is current first.

If data really is important you should have backups anyway. Systems fail. And anytime we make changes sometimes bad things happen and having a good backup is the only way to recover. So make a good backup. I use rsync to copy to another drive on my desktop, copy some data to flash drives since they have dropped in price and copy most important data to DVDs so I have an image that is from older dates in case I overwrite something and lose it.

I am not sure how you are booting now? With UEFI the first partition is a FAT32 efi partition. And with BIOS boot on gpt drives you have to have a bios_grub partition for grub to install correctly. Did you force a grub install with blocklists which is not recommended?

It looks either way you have to do some major reorganization of hard drive.

---

### Post by oldfred on 2013-05-07
this user was not able to install in UEFI mode and converted his Windows to MBR.

 ASUS-K55N is just not able to boot an EFI linux, converted to BIOS with MBR partitioning - UEFI Windows 7
[http://ubuntuforums.org/showthread.php?t=2061646&p=12635283#post12635283](http://ubuntuforums.org/showthread.php?t=2061646&p=12635283#post12635283)

---

