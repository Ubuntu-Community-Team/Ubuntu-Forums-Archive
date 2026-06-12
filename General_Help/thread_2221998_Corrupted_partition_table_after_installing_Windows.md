---
title: "Corrupted partition table after installing Windows 7"
date: 2014-05-04
forum: General Help
---

### Post by nonce0013xch on 2014-05-04
I've been using various forms of Ubuntu, sometimes with Windows XP on the same disk, pretty happily since 2007. On my current laptop, a Toshiba Satellite I got in late 2010, I've been using only Kubuntu (actually Ubuntu with KDE packages) for a while, but I'd left about 150 gigs of my 465-gig hard disk unallocated when I originally installed Ubuntu so I could later install Windows if I wanted to. Yesterday, I proceeded to install Windows 7 on that unclaimed space. This apparently succeeded. GRUB's menu no longer appeared at startup, so I tried to use Boot-Repair-Disk. This succeeded according to Boot-Repair's messages, but booting the machine still went directly to Windows.

I then noticed from a peek at GParted while booted from Boot-Repair-Disk that the interval of the disk where there was supposed to be a logical partition for Linux was listed as "unallocated". Apparently, Windows 7 uses another partition (the system partition, I think; [http://windows.microsoft.com/en-us/windows/what-are-system-boot-partitions#1TC=windows-7](http://windows.microsoft.com/en-us/windows/what-are-system-boot-partitions#1TC=windows-7) ) in addition to the one you select when you install it, possibly clobbering whatever's there. I tried to use TestDisk to resurrect the deceased partition. Apparently I did it wrong, since my laptop then became unbootable. I tried again after booting from Boot-Repair-Disk again, and now everything works!… sort of.

You see, I now get a GRUB menu with an entry for Ubuntu and (two) entries for Windows at startup. I am now running Ubuntu and it seems to work fine. I haven't tried Windows again. However, Ubuntu complains that the root filesystem has "serious errors" at startup, and GParted is now showing my whole disk as unallocated. GParted also gives a warning message "Can't have overlapping partitions".

I've seen several other threads that describe a situation that I think is like mine, such as [http://ubuntuforums.org/showthread.php?t=2000282](http://ubuntuforums.org/showthread.php?t=2000282) , but there do seem to be differences and I'm afraid to do more unaided mucking about in case I make things worse.

Here's an up-to-date boot-info file from boot-repair: [http://paste.ubuntu.com/7395018/](http://paste.ubuntu.com/7395018/)

So, I now have two questions:

1. What should I do about this inconsistent partition table? Is there anything I can do other than wiping the whole disk and reinstalling everything? I have backups, but this would still be a considerable inconvenience.

2. Is it safe to try either of two the Windows entries in GRUB, or might Windows corrupt the Linux partition again if I run it?

---

### Post by oldfred on 2014-05-04
This is the corruption.
 /dev/sda1 overlaps with /dev/sda2
Note that sda6's end is one sector less than sda2's, and that should be then end of the sda1 also.

      
 ```
/dev/sda1               2,047   [COLOR=#ff0000]664,801,829[/COLOR]   664,799,783   f W95 Extended (LBA)
/dev/sda5               2,048   660,602,879   660,600,832  83 Linux
/dev/sda6         660,604,928   664,797,183     4,192,256  82 Linux swap / Solaris
/dev/sda2 [COLOR=#ff0000]        664,797,184[/COLOR]   665,001,983       204,800   7 NTFS / exFAT / HPFS

```
The end of sda1 cannot be after the start of sda2.


 First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

Many partition tools calculate the extended partition entry and just re-saving may correct it.

      
 this occasionally fixes issues and is worth trying:
you do the following :
fdisk /dev/sda
use option : x (expert mode)
use option : p (to print)
use option : v to verify partition
if it is ok
then you can do
option : w ( to write table to disk)
option : q to quit

     

Fixparts is not for overlapping partitions, but again it recalculates table and since in your case it is the extended it may work also.
      
 Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Windows normally creates the hidden in Windows 100MB boot partition. It also has Windows recovery (repair or f8). But many users just delete it as they do not know it is essential. So Boot-Repair copies boot files to main install and then grub2's os-prober finds both. You can boot either and f8 may not work if booting the 100MB form grub as it is very quick. Best just to use Windows to make its own repair flash drive.

      
 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by nonce0013xch on 2014-05-04
Thanks for your prompt and informative reply.

The fdisk routine had no effect. Fixparts, on the other hand, seems to have indeed fixed the overlap, hooray! Here's how things stand now: [http://paste.ubuntu.com/7395865/](http://paste.ubuntu.com/7395865/) . However, I'm still getting the "serious errors" message on startup, and while GParted now shows what looks like the correct partition table, it shows these error messages first:

- "Error informing the kernel about modifications to partition /dev/sda1 -- Device or resource busy.  This means Linux won't know about any changes you made to /dev/sda1 until you reboot -- so you shouldn't mount it or use it in any way before rebooting."

- "Failed to add partition 1 (Device or resource busy)"

So it seems that not all is well.

---

### Post by oldfred on 2014-05-04
Not sure what it is complaining about.
But it is a bit unusual to have the extended partition first. And also to have grub in the PBR - partition boot sector of the extended partition. You normally do not install grub to a partition.

Did you run fixparts from your working system? I think it is supposed to run from live installer. So that may be why it is giving warnings as saved internal partition data is different than partition table?

---

### Post by nonce0013xch on 2014-05-05
> **oldfred said:**
> Did you run fixparts from your working system?
Yes, I did. I've now done it again while booted from the Boot-Repair-Disk instead, but nothing seems to have improved. Here's where things stand now: [http://paste.ubuntu.com/7401027/](http://paste.ubuntu.com/7401027/)

---

### Post by oldfred on 2014-05-05
You are not using UUIDs. And any partition change then means you have to manually edit fstab. It seems root & swap are reversed.

fstab says sda6 is /
 /dev/sda6       /               ext4    errors=remount-ro,user_xattr 0       1
/dev/sda5       none            swap    sw              0       0

But partition table says sda5 is root.

   /dev/sda5               2,048   660,602,879   660,600,832  83 Linux
/dev/sda6         660,604,928   664,797,183     4,192,256  82 Linux swap / Solaris

---

### Post by nonce0013xch on 2014-05-05
Good catch, thanks. I fixed fstab. Now the error at startup is gone, although GParted gives the same messages as before.

By the way, I tried booting into Windows 7 (both GRUB entries) and got the following error from Windows Boot Manager:

> Status: 0xc000000e
Info: The boot selection failed because a required device is inaccessible.

---

### Post by oldfred on 2014-05-05
Grub only really boots working Windows. The partition changes may have also messed with it. 
You probably need a Windows repair CD or flash drive.
A few have booted into Windows recovery (repair) with f8 but you have to press f8 at almost the same time, but just after grub entry for Windows boot partition, your sda2. Usually easier to use Windows repairCD.

You also may be able to install Windows boot loader to MBR temporarily. Make sure boot flag is on sda2 as that is boot partition. It looks like you have boot files in sda3, but not sure if that also has a repair/recovery or not for f8 to work there. Then after fixing Windows you can reinstall grub to MBR.

---

### Post by nonce0013xch on 2014-05-06
In lieu of a repair disk, I tried booting from my Windows install disk and using its own "Repair this computer" button. Lo and behold, Windows now boots, and the GRUB menu still shows up on startup and Ubuntu still works, as well. Thanks again for all your help.

I think I'll hold off on marking this thread as solved in case anybody can figure out what GParted is complaining about and if it indicates any trouble that might crop up later.

Boot info again: [http://paste.ubuntu.com/7407413/](http://paste.ubuntu.com/7407413/)

---

### Post by oldfred on 2014-05-06
What is gparted complaining about.
It would not have worked with the partition issue that you fixed.
It does complain if Windows needs chkdsk or is hibernated as the Linux NTFS driver does not mount NTFS unless everything is ok.

---

### Post by nonce0013xch on 2014-05-06
Sorry if I was unclear. I was referring to these messages I quoted earlier:

- "Error informing the kernel about modifications to partition /dev/sda1  -- Device or resource busy.  This means Linux won't know about any  changes you made to /dev/sda1 until you reboot -- so you shouldn't mount  it or use it in any way before rebooting."

- "Failed to add partition 1 (Device or resource busy)"

/dev/sda1 is the extended partition, so presumably this is unrelated to the two NTFS partitions.

---

### Post by oldfred on 2014-05-06
Is gparted showing that just on loading?
It would show errors from a gparted on a working system, or any mounted partitions including an extended partition from a working install. Any mounted partition including swap as a logical then also mounts the entire extended partition. And even the live installer usually mounts swap and you have to unmount it to edit partitions from live installer.

Is there some left over change it wants to process, but has not cleared? Never seen that, but cannot explain error.

---

### Post by nonce0013xch on 2014-05-07
> **oldfred said:**
> Is gparted showing that just on loading? Yes, and it otherwise seems to work fine.  > Is there some left over change it wants to process, but has not cleared? Not so far as I can tell.

I notice that the windows showing the error messages are titled "Libparted bug found!". Also, I tried KDE's partition editor and it doesn't complain about anything. Looks like the problem is indeed some bug in GParted or libparted rather than something wrong with my disk, so I'll mark this as solved.

---

### Post by oldfred on 2014-05-07
Glad you got things working.

I do have multiple orisons of gparted, besides the version in my various Ubuntu ISO, I download a gparted live ISO and parted magic's live ISO.

---

