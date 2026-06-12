---
title: "Fixing MBR and booting Windows"
date: 2008-05-29
forum: General Help
---

### Post by Kuniva on 2008-05-29
I need help with getting booting my Win XP.

I had to reset BIOS settings and it deleted my windows bootloader. Now I get GRUB error 22. I cannot load Ubuntu because ita old 6.10 installation and it doesnt work. So I loaded 6.06 LiveCD and I'm writing this from it. Before i used SuperGRUB to fix my MBR but now i cant because i no longer have it and i cannot burn another copy because LiveCD is in my DVD Burner. SO i tried MS-sys as sugested in [this post]("http://ubuntuforums.org/showthread.php?t=616540#2") replacing /dev/sda with /sda1 as my fdisk -l suggested that sda1 is Windows partition but i get:
```
ubuntu@ubuntu:~$ sudo ms-sys -m /dev/sda1
/dev/sda1 seems to be a disk partition device,
use the switch -f to force writing of a master boot record

```

What should i do?

Here is my fdisk -l:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11749    94373811    7  HPFS/NTFS
/dev/sda2           11750       19293    60597180   83  Linux
/dev/sda3           19294       19457     1317330    5  Extended
/dev/sda5           19294       19457     1317298+  82  Linux swap / Solaris

Disk /dev/hdd: 20.0 GB, 20020396032 bytes
16 heads, 63 sectors/track, 38792 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System

```

Thanks for any help.

---

### Post by geo909 on 2008-05-29
Try super grub disk.
It fixes/installs/reinstalls grub automagically.
I haven't used it but it's quite popular round here,
so maybe you want to give it a try..

EDIT: SORRY!! I didn't see that you had a problem with supergrub..
But there is also a [USB stick version]("http://www.supergrubdisk.org/index.php?pid=7"), so if you have one give it a try.

---

### Post by Kevbert on 2008-05-29
If you're going to install Ubuntu then just let it create a new bootloader (hopefully it will see XP).  I'd recommend a manual install if you don't have a free empty partition.  System partition should be at least 10Gb, partitioned ext3, mount point /  The swap file should be 2 x your ram memory.
If your not going to install Ubuntu then you need to use your Windows XP install CD.  Boot that and let it run until you get the option to go into [COLOR="Red"]recovery mode[/COLOR]. Select this and at the prompt enter
```
fixmbr
fixboot

```

---

### Post by geo909 on 2008-05-29
There is [a very good ubuntu-guide]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") for cases like yours. I had found it useful when I had a similar problem.

 But I would recommend to check the usb version of super grub disk first.

---

### Post by Kuniva on 2008-05-29
I appriciate response.
> **geo909 said:**
> Try super grub disk.
It fixes/installs/reinstalls grub automagically.
I haven't used it but it's quite popular round here,
so maybe you want to give it a try..

EDIT: SORRY!! I didn't see that you had a problem with supergrub..
But there is also a [USB stick version]("http://www.supergrubdisk.org/index.php?pid=7"), so if you have one give it a try.

I should have made myself more clear. I was in hurry while writing OP so it probably doesn't make as much sense as it should.

I need to re-install Windows Boot-Loader back into Master Boot Record. Its no use to re-install GRUB, Ubuntu installation itself isn't working. I used SuperGRUB before because it has option to automatically restore Windows Loader. Now, I no longer have that disk with SuperGRUB on it and I cannot burn another one because LiveCD has locked my DVD Burner. Sadly I have no floppies or USB Stick so i cannot use other versions of SiperGRUB. THats why I looked into using ms-sys.

> **Kevbert said:**
> If you're going to install Ubuntu then just let it create a new bootloader (hopefully it will see XP).  I'd recommend a manual install if you don't have a free empty partition.  System partition should be at least 10Gb, partitioned ext3, mount point /  The swap file should be 2 x your ram memory.
If your not going to install Ubuntu then you need to use your Windows XP install CD.  Boot that and let it run until you get the option to go into [COLOR="Red"]recovery mode[/COLOR]. Select this and at the prompt enter
```
fixmbr
fixboot

```
Not going to install Ubuntu because I'm not only user of this computer and it needs to be up and running asap. And I do not have XP recovery disk (I do but its in no working condition).

> **geo909 said:**
> There is [a very good ubuntu-guide]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") for cases like yours. I had found it useful when I had a similar problem.

 But I would recommend to check the usb version of super grub disk first.

That guide doesn't help me because it shows various ways to reinstall GRUB. I need to reinstall Windows Boot Loader. And once again, USB is not an option.

Thanks for response.

---

### Post by Kevbert on 2008-05-29
You can also get supergrub on floppy, see [http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

---

### Post by geo909 on 2008-05-29
Ok, I understand now..
I am afraid I cannot help you with this. Hope you find a solution..

---

### Post by Kuniva on 2008-05-29
Ok, so I went out and bought last pack of floppies in my local shop. When I put it in Ubuntu LiveCD doesn't recognise it at all. I assume i have to mount it but I don't know how. I tried to follow [Herman's]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_Make_your_Super_Grub_Floppy_Disk") advice but once I execute command terminal just sits there, I couldn't notice any floppy activity. I assume it needs to be mounted. Anyone can help?

---

### Post by Kuniva on 2008-05-29
Bump

Anyone?

---

### Post by meierfra. on 2008-05-29
The correct command is

```
sudo ms-sys -m /dev/sda
```
(so sda in place if sda1)

---

### Post by Kuniva on 2008-05-30
> **meierfra. said:**
> The correct command is

```
sudo ms-sys -m /dev/sda
```
(so sda in place if sda1)
Tried that and and i get message that operation was done sucessfully, and when i try booting Grub appears as if nothing was done.

---

### Post by Kuniva on 2008-05-30
Ok, update!

I tried to reinstall GRUB in hope it would detect Windows. I followed [this post]("http://ubuntuforums.org/showthread.php?t=224351") and it got me one step further. Now I don't get error 22 straight after  stage 1.5, now it shows up after I select XP in menu.

So I got my friend to burn me a copy SuperGRUB CD and I tried to Fix MBR. It retuned new error "invalid partition table". By the looks of it my problem whent even further. So I removed SuperGRUB disc and tried to get to error 22 again. Now I cant even get to GRUB, Invalid partition tabe shows up at point when GRUB stage 1.5 should. So I reinstalled GRUB once more following above link. It gave me same error, but this time it shows up when I select XP in GRUB menu.

I'm out of ideas and time. I'm starting to become desperate. Maybe trying Ubuntu wasn't best decision...

---

### Post by meierfra. on 2008-05-30
Edit: Read my next post first. It might solve your problem.

FixMBR from SuperGrub deleted Grub from the MBR.  That's why you don't get error 22 anymore.


You might try to fix your partition table with testdisk (see my signature)

---

### Post by meierfra. on 2008-05-30
> Tried that and and i get message that operation was done sucessfully, and when i try booting Grub appears as if nothing was done.

Very strange. Any chance that you are booting from your 20GB drive?  


I think that is indeed your problem. You reset your Bios,  and now the 20GB drive is first in the boot order. That would also explain the "invalid partition table". Your 20GB drive has no partition table.  Just change  the boot  order in the bios.  (or remove the 20GB drive)

---

### Post by Kuniva on 2008-05-30
Thanks for trying to help.

No, it looks like ms-sys did nothing, SuperGRUB disk did. It fixed it and placed windows boot loader. It looks to me like partition table problem is separated from bootloader issue. Anyway, I went to BIOS and cheked Boot menu. Under it there is Hard Disk Priority submenu. It only has my SATA drive showed there as first Hard Disk to look for. IDE isn't even displayed. So just for good mesure I pulled power cable out of my 20gig IDE HD and tried again. Still the same.

Also, I red that corrupted partition table can happen if you have 2 active partitions. So I loaded my sysrescueCD and opened qtParted. It showed my SATA drive and Windows partition as only active one. I did that while IDE HD was still connected and qtParted didn't even find it (IDE HD) and show it as free partitionless space.

And finally I also tried to boot Windows from SuperGRUB menu. As you probably know there you can select partition witch has Windows and let SuperGRUB attemp to load it. Nothing, still "Invalid Partition Table".

I'm now gonna try checking HD as you suggested in first post.

Thanks for response.

Edit:I don't really get how link you provided is going to help. I didn't delete any partitions. Both Ubuntu LiveCD and qtParted can see 'em all and I can mount ext3 partition in liveCD. I could probably mount NTFS partition as well if I installed NTFS r/w software. If you could explain it in bit more details I would be greatful.

---

### Post by Kuniva on 2008-05-30
Thanks for help, I solved my problem. See [this]("http://ubuntuforums.org/showthread.php?t=812715") for answer.

I figured its separate problem, when I used sudo ms-sys -m /dev/sda1/ program told me that I could force it to install bootloader with -f. And so I did it, corrupting my NTFS partition.

Windows recovery disc fixed it as shown in that link.

Thanks for all the help, I appreciate it.

---

### Post by meierfra. on 2008-05-30
Sorry, it seemed like you never used "sudo ms-sys -m /dev/sda1". You should have told us.
Yes, that destroys the boot sector of your windows partition and fixboot will restore it.

I'm still puzzled  though why "ms-sys" did not erase Grub. Oh, well.

---

### Post by meierfra. on 2008-05-30
> Edit:I don't really get how link you provided is going to help. 

You got the "Invalid Partition Table"  message, and Testdisk can rebuild your partition table. I didn't had much hope though, since from your "fdisk -l" where did not seem anything wrong with your partition table.
Also I did not know that a corrupt boot sector could cause an ""Invalid Partition Table" message.

But testdisk actually could have  solved your problem. An NTFS partition  keeps a  backup of the boot sector. Testdisk can use the backup  to restore you boot sector.  You have to use the "advanced" option rather than "analyse".

---

