---
title: "Ubuntu 14.0..won't load after security update. Help."
date: 2015-07-08
forum: General Help
---

### Post by techqueries on 2015-07-08
I was trying to get Flash to work on Prime Amazon - I did the following:
 

 sudo apt-get install hal libhal1
 

 sudo apt-get install hal
 

 cd ~/.adobe/Flash_Player
 

 rm -rf NativeCache AssetCache APSPrivateData2
 

 At the same time I accepted a security update. At the end of which, I followed the prompt to reboot. And now Ubuntu won't load. I get the message below.
 Please help. Thanks.

 

 --------------------------------------------------------------
 Gave up waiting for root device. Common problems:
 ... ...(shows a list of three common problems)
 ALERT! /dev/disk/by-uuid/(a long id) does not exist. Dropping to a shell!
 BusyBox v1.13.3 ...
 (initramfs)
 --------------------------------------------------------------

---

### Post by techqueries on 2015-07-08
Wow. I've been using Ubuntu for 4 years now; Been very happy with it because I never encountered any problems.
Now that I run into one - I have NO CLUE how to fix this.
And my entire life is in this computer. My last back up was a month ago. I can't afford to lose any data.

Is there no way to fix this?

---

### Post by Dennis N on 2015-07-08
If you can boot to the grub menu see if you can boot a older kernel (under 'Advanced options for Ubuntu'). Hold shift key down while booting if necessary to get the menu to appear. The UUIDs may have been changed somehow on the current kernel during the recent grub version upgrade.

---

### Post by techqueries on 2015-07-08
Thanks Dennis for your response.
When I boot with an older kernel - straight or in recovery mode....it runs through the process and ends with the same message with 3 additional lines 

                        

 *****************************************************

 [I] gave up waiting for root device. common problems:
[/I]
[I]alert! /dev/disk/by-uuid/26c62cfd-a7d7-4675-bee7-bf48e177ea2 does not exist. Dropping to a shell!  

[/I]
*[  66.202263] hidraw: raw HID events driver (c) Jiri Kosina*
*[  66.207552]  usbcore: registered new interface driver usbhid*
*[  66.207614]  usbhid: USB HID core driver*

**********************************

From this link here ( [http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html](http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html) ) is reasoning that it has to do with the initrd.img file having changed after upgrade resulting in missing modules/drivers.
I don't know  is the related to UUIDs?

---

### Post by Dennis N on 2015-07-08
**I don't know is the related to UUIDs?**
I thought it might be, since it can't locate the root partition by UUID (if I interpret that right). This cause is mentioned in Dedoimedo's article under "Check root=" section. Which he dismisses. So did you explore the missing modules idea?  I don't know what I could add to what he has there. Smart guy who (mostly) writes good stuff.

---

### Post by techqueries on 2015-07-08
I was figuring how to get out of the below screen that I land on each time I power up the computer 

[I]Gave up waiting for root device. Common problems:
 ... ...(shows a list of three common problems)
 ALERT! /dev/disk/by-uuid/(a long id) does not exist. Dropping to a shell!
 BusyBox v1.13.3 ...
 (initramfs)[/I]

I boot with the LiveCD I installed ubuntu with last September and manage to power up the computer. From there I can see the files from my Windows OS. But nothing from my Ubuntu OS.

I'm thinking I could copy the initrd.img from the cd to the hardrive Ubuntu....but how do I go about doing that?

in fact, the 3 additional messages in the boot-failure appear to refer to the drivers as well, if I understand correctly

---

### Post by techqueries on 2015-07-08
okay, the writer is correct that it has to do with the initrd.img file being altered.

I was able to boot with livecd. I went to the file system and see indeed that a new initrd.img replaced the original one today at 9 am (See attached image).

So now what?

Do I simply revive the original initrd.img which is at present named initrd.img.old and overwrite the defective initrd.img?

If so, how do I do that? I don't have permissions to do anything in my Ubuntu hardrive from the live cd.

---

### Post by Dennis N on 2015-07-08
> I'm thinking I could copy the initrd.img from the cd to the hardrive Ubuntu....but how do I go about doing that?
I don't think that would work. I think Dedoimedo's article said the initrd.img he copied was from exactly the same kernel version? I think that would matter. A new one is generated for each kernel. All his 4 ubuntus were identical, and up to date with the same kernel version. Don't think he mentioned what he would do with only one Ubuntu.

Those entries initrd.img and initrd.img.old are symbolic links that point to files in /boot:

From my computer (irrelevant lines of output eliminated):

```
dmn@Roxanne:/$ ls -l
lrwxrwxrwx   1 root root    33 Jul 31  2014 initrd.img -> boot/initrd.img-3.11.0-26-generic
lrwxrwxrwx   1 root root    34 Jul 31  2014 initrd.img.old -> /boot/initrd.img-3.11.0-26-generic
 
```
The Debian handbook ( [https://debian-handbook.info/browse/stable/sect.kernel-installation.html](https://debian-handbook.info/browse/stable/sect.kernel-installation.html) ) says these point to the newest and previous versions, but mine have the same target, so I don't get that. 

Two last ditch ideas:
Do you have room for a dual boot? You could simply install another Ubuntu on a new partition and copy your files over from the broken OS. Maybe a last resort if no other solution is found? (Probably what I would do because it's the least technical and possibly easiest).  
Your files are probably safe in any case. If not the dual boot idea, you could access them with a live cd and copy them off to a flash drive or USB hard drive for safety.

I hope someome else will have more informed suggestions for you.

---

### Post by techqueries on 2015-07-08
I did think about doing as you say. copying my files from live cd. But I run into the problem of permissions. I can,t get access. Plus there is all my files and passwords from Thunderbird that I don't know how to copy.

I'm reading something from this page: [http://askubuntu.com/questions/465826/system-doesnt-boot-anymore-error-file-initrd-img-3-11-0-20-generic-not-found..it](http://askubuntu.com/questions/465826/system-doesnt-boot-anymore-error-file-initrd-img-3-11-0-20-generic-not-found..it) gets me a little closer...

---

### Post by Dennis N on 2015-07-08
Files you own should have read permission for 'other' (anyone) by default. Which means anyone can copy the file. The flash drive has to be FAT32 to be able to paste the files to it. Even if 'other' doesn't have read permission on some files, you can give 'other' permission to read with **sudo chmod [options] filename**, then you can copy them. I tested this using the live USB installer and a FAT32 flash drive to copy the files to just to be sure. It works.

---

### Post by Dennis N on 2015-07-09
Left this out:

Did my copying between two file manager windows in the live USB installer. In one, mounted my OS partition from the side pane, and navigated to my home folder. In the other, I mounted the flash drive from the side pane for copying to. That's it.

---

### Post by techqueries on 2015-07-09
Not sure what I did that **solved** the problem last night. I booted with livecd and followed instructions on this webpage -  [http://askubuntu.com/questions/465826/system-doesnt-boot-anymore-error-file-initrd-img-3-11-0-20-generic-not-found](http://askubuntu.com/questions/465826/system-doesnt-boot-anymore-error-file-initrd-img-3-11-0-20-generic-not-found)

One out of every 3 commands in the instructions didn't process. So I  just stopped at apt-get update. I said I'd just try again tomorrow  morning. But this morning looks like whatever I did seems to have  worked. I booted up normally. Hope this helps somewhat for those who run  into this type of problem in the future.
[I]
Boot live-system and gather information

It is the same you did when installing Ubuntu. Just make sure to chose  "Try Ubuntu". When you see the desktop, open a terminal (CTRL+ALT+T) and  run the following:

sudo blkid

which will give you a result like this

/dev/sda1: LABEL="EFI" UUID="70D6-1701" TYPE="vfat" 
/dev/sda2: UUID="68ca53b3" LABEL="OSX" TYPE="hfsplus" 
/dev/sda3: UUID="49526001" LABEL="Recovery HD" TYPE="hfsplus" 
/dev/sda4: LABEL="BOOTCAMP" UUID="FCF67D7DF67D394A" TYPE="ntfs" 
/dev/sda6: UUID="c1c76922" TYPE="ext4" 
/dev/sda7: UUID="3b171268" TYPE="ext4" 
/dev/sda8: UUID="bf3dd1b7" TYPE="swap"

Please post the result of this command back here, so that we can help you further. I will continue with the above example.
Chroot into the installed system

With chroot you can use a live linux and switch to the Linux installed  on your harddrive to repair it. It is important whether your system uses  EFI or BIOS. If you have/had Windows 8 on the machine, it is a good  indicator for EFI. In the example above there is a small vfat partition  that is even called EFI so the above system uses EFI to boot. The two  ext4 partitions are Linux partitions. You can just open them from the  launcher to see which one contains to root filesystem (contains folders  like etc, usr, var, ...). In the above case /dev/sda6 is the root  partition and /dev/sda1 is the EFI partition.

In a terminal run the following commands to prepare and open the chroot.

sudo -i
mount /dev/sda6 /mnt
mount /dev/sda1 /mnt/boot/efi
for i in dev dev/pts proc sys sys/firmware; do mount --bind /$i /mnt/$i; done
chroot /mnt[/I]

[I]The EFI partition only needs to be mounted if EFI is actually used, otherwise you can omit that line.

The list of partitions you posted indicates you use LVM, so we need to  account for that. Replace the two mount commands above with these:

mount /dev/mapper/ubuntu--vg-root /mnt
mount /dev/sda1 /mnt/boot

Repair

To repair your system continue to run the following commands.

apt-get update

----------------------------------------------------------------------------------------
[/I]
Thanks for your help Dennis*. *When I boot into the OS normally, I have no problem copying and transferring files from the folders to flash drives.But when I'm trying to get into those files from an external OS - like the live cd* - *I'm not allowed access. The folders won't even open. A pop-up window informs me I do not have "permissions".

Anyway, for now I don't need to do that. As everything is resolved and back to normal. Cheers!

---

