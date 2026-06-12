---
title: "dd command for creating iso file."
date: 2021-03-21
forum: General Help
---

### Post by gardenair on 2021-03-21
I have a bootable USB stick (8 GB is its size) containing windows 10 inside it. I want to use it in my VirtualBox.For that purpose, I create an iso file using the dd command but before it, I use** lsblk **command to see what Ubuntu looks like that drive.

sdb      8:16   1   7.3G  0 disk 
&#9492;&#9472;sdb1   8:17   1   7.3G  0 part /media/test/v7283743

By using the command I am just showing the output of the use drive # df -hT

[B]Filesystem     Type        Size  Used  Avail  Usage%    Mount on 
[/B]
/dev/sdb1      fuseblk      7.4G  2.5G   4.9G     35%          /media/test/v7283743


My dd command is 

# dd if=/dev/sdb1 of=/home/test/Downloads/Windows10_Lite.iso
15354112+0 records in
15354112+0 records out
7861305344 bytes (7.9 GB, 7.3 GiB) copied, 605.777 s, 13.0 MB/s

Well, I create an iso file in the destination folder which is the same size as the USB stick. My windows bootable files data was approx 4 GB 
and remaining space was free in the USB [U]so why** dd **create the ISO file the same as the USB stick size?
[/U]
2- When  I try to connect that iso file with my virtual box machine it says " **FATAL No bootable Medium Found !System Halted**"

Can you please me that where I am doing a mistake so I may fix it?
Thanks

---

### Post by Impavidus on 2021-03-21
1: The dd command copies the entire filesystem, not just the part used for files.

2: I've not that much experience with virtual machines, but my guess is that your .iso must be a copy of the entire device (including partition table), not just of the filesystem used in the bootable windows disk.

---

### Post by gardenair on 2021-03-21
well at the moment my concern is only to create an iso file. Keep aside Virtual Machine for a moment.
Does this mean if I have a USB of  64 GB containing only windows 10 bootable files **dd **command will create a 64 GB iso file? If yes it is the wrong thing. what is the correct way for creating an iso file?

---

### Post by dinkidonk on 2021-03-21
In your command, dd sees /dev/sdb1 as a file with the size 7.3GiB. Had the USB stick been 64GB so would the image created therefrom with dd. The dd command will not remove unused space, you need another tool for that. You could also shrink the file system and the partition prior to the dd command.

The reason for the VM not booting may be that your image does not contain the boot loader which is located prior to the partition(s), so instead of dd /dev/sdb1 you would need to dd the entire drive ( /dev/sdb ). But again, I'm sure there are better tools for the job than dd.

---

### Post by mikewhatever on 2021-03-21
First, you've told dd to copy the content of /dev/sdb1, and it did just that.
Second, Microsoft provides Windows ISOs, just download it. Not sure where dd comes in.

---

### Post by dinkidonk on 2021-03-21
> **mikewhatever said:**
> Second, Microsoft provides Windows ISOs, just download it. Not sure where dd comes in.

If he wants to keep his installation of Windows, an ISO from MS is not an option.

---

### Post by mikewhatever on 2021-03-21
> **dinkidonk said:**
> If he wants to keep his installation of Windows, an ISO from MS is not an option.

An installation of Windows 10 would never fit on an 8GB flash drive. You'd need at least 4 times the size, and forget about updates.
An ISO of Windows, however, does fit, which is, apparently, what it is.

---

### Post by dinkidonk on 2021-03-21
> **mikewhatever said:**
> An installation of Windows 10 would never fit on an 8GB flash drive. You'd need at least 4 times the size, and forget about updates.
An ISO of Windows, however, does fit, which is, apparently, what it is.

You are probably right. I've not been into Windows for a long time and I was not aware if there was such a thing as "Windows Lite" with limited space usage ;)

---

### Post by mikewhatever on 2021-03-21
> **dinkidonk said:**
> You are probably right. I've not been into Windows for a long time and I was not aware if there was such a thing as "Windows Lite" with limited space usage ;)

Well, 32GB is the "limited space usage", exactly the requirement for Windows lite. :lolflag:

---

### Post by yancek on 2021-03-21
If you have windows 10 lite on a bootable usb, why would you want to create an iso?  Just use the VBoxManage command to boot the usb directly in VirtualBox.  Plenty of site with tutorials on how to do this.

---

### Post by Impavidus on 2021-03-22
I don't know how your bootable usb was created. If it was created using dd or something like that, some information was lost when creating the bootable usb: the size of the original .iso. But if you know for sure that it was less than 5GB, you can tell dd to copy exactly 5GB and it should work. If the bootable usb was created using some other tool, it's impossible to say. As the file system on the usb is 7.4GB, it appears this was not created using a simple file copy, so the latter seems to be the case and you have to copy all of it to create a usable .iso.

A virtual machine can boot from an .iso file. Your usb drive is a file with the same contents as the .iso you want to create from it. So the virtual machine can boot from the usb drive too. The only advantage of first copying the usb to an .iso is that the latter may run a bit faster. And indeed, you have to copy from the very beginning of the drive, to make sure you include the bootloader.

---

### Post by TheFu on 2021-03-22
Can Windows run from read-only media?  IDK. I've never seen that outside the installer.

dd has bs= and count= options. These can be used to limit how much data is copied, but dd is stupid. It expects the admin to know where the data is inside the device, which can seldom be determined from Windows.

---

### Post by ajgreeny on 2021-03-22
Surely dd can not create an .ISO image but it's often used to copy byte for byte from an .ISO to a USB.

I think the OP has either asked the wrong question or is totally confused about using dd with .ISO image files.

---

### Post by gardenair on 2021-03-22
Thanks for your replies.I doesn't know a lot about  dd command .For the simplicity of my question I have  have a usb  contain some data and i want to make an iso file so I may burn DVD with it  now which tool may I use for that  ?

---

### Post by TheFu on 2021-03-22
> **gardenair said:**
> Thanks for your replies.I doesn't know a lot about  dd command .For the simplicity of my question I have  have a usb  contain some data and i want to make an iso file so I may burn DVD with it  now which tool may I use for that  ?

There are probably 5 GUI tools for burning optical disks. **K3b** comes to my mind, but I haven't used it in at least a decade. There's a website - alternativeto.net which can be used to enter a tool you know and find ... er ... Alternatives To it. Then filter by OS.

There's also **genisoimage**.
```
NAME
       genisoimage  -  create  ISO9660/Joliet/HFS filesystem with optional Rock Ridge
       attributes

SYNOPSIS
       genisoimage [options] [-o filename] pathspec [pathspec ...]
```

I have serious doubts that Windows can be run from a read-only format - which is what an ISO file system is.  A currently running Windows will have settings that point to the swap file, which will also be read-only inside the ISO.  That can't be good.  OTOH, you'll not know until you try.  Could be fun.

---

### Post by ajgreeny on 2021-03-22
Having created an iso file of the various files and folders of your choice, which is quite easily done using most CD burner applications, what exactly do you want to do with it.

Simply creating an .iso file from them will not mean that it is a bootable image iso if that's what you are tring to do; that is quite different.

---

### Post by gardenair on 2021-03-24
Well my primary concern is not to create any boot-able ISO image. I want that any data in the USB (if there is any boot-able OS files or any sort of picture)  may convert into iso image.
Yes there are many GUI app to burning or creating ISO file but i am interested to do it via terminal command.if there is any utility then it will be nice otherwise will use GUI .

Thanks.

---

### Post by BFG on 2021-03-24
Check out bootiso: [https://www.2daygeek.com/bootiso-a-simple-bash-script-to-securely-create-a-bootable-usb-device-in-linux-from-iso-file/](https://www.2daygeek.com/bootiso-a-simple-bash-script-to-securely-create-a-bootable-usb-device-in-linux-from-iso-file/)
You could alter the script for your needs.


Personally i wouldn't bother with any of that.  A VM can directly access data on a USB stick plugged into the host machine, no need for said files to be inside an ISO.

---

### Post by aug7744 on 2021-03-24
@gardernair All good with you ? You need start Virtual Box with sudo to have USB drive access. sudo virtualbox. I had the same issue and using the command above was possible start USB.

---

### Post by ajgreeny on 2021-03-24
> **aug7744 said:**
> @gardernair All good with you ? You need start Virtual Box with sudo to have USB drive access. sudo virtualbox. I had the same issue and using the command above was possible start USB.
**NO, NO, NO!  That is potentially very dangerous and should never be done.**

There is absolutely no need to run VBox as root to have access to a USB drive attached to the host; what you do need is to add the Guest Extension pack the most recent of which you get from [https://download.virtualbox.org/virtualbox/6.1.18/Oracle_VM_VirtualBox_Extension_Pack-6.1.18.vbox-extpack](https://download.virtualbox.org/virtualbox/6.1.18/Oracle_VM_VirtualBox_Extension_Pack-6.1.18.vbox-extpack) to the VBox program itself than add the guest additions to your guest VM.

---

### Post by TheFu on 2021-03-24
> **ajgreeny said:**
> **NO, NO, NO!  That is potentially very dangerous and should never be done.**
 
+1.  If an end-user program needs sudo, something is wrong, screwed up or misconfigured  - unless it is specifically a system admin tool like gparted.  That's about the only GUI program I can think of that needs to be run with **sudo -H**.

---

