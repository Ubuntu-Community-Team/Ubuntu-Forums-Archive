---
title: "Win 7 and 12.10 cloned to SSD...grub in MBR not cloned...how to repair / reinstall?"
date: 2012-12-29
forum: General Help
---

### Post by tedrogers on 2012-12-29
Hi all,

As in the title, I had a smaller ATA disk and cloned each partition to a new and larger SSD using CloneZilla. It took a good few hours, but that part of things is done and I marked the first partition as bootable in GParted.

Trouble is I have not cloned the MBR with Grub2 loader (for obvious reasons, the main one being that the MBR is device/HD specific, and that copying an MBR from one drive to another could spell serious trouble!) so now I am stuck with no way to access my Ubuntu install on /sda3. Partition table is as follows:

/sda1 Win 7
/sda2 Swap
/sda3 /
/sda4 /Home

How can I reinstall Grub2 without access to Ubuntu? I've done a bit of research here:

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

Am I correct in thinking I can run the Boot-Repair live CD, and that this will detect all my partitions / installs and rebuild a Grub2 loader for me and place it in the MBR of /sda1?

Thanks for any help. Really looking forward to seeing how this SDD hard disk improves the performance of my ageing laptop.

Thanks.

---

### Post by oldfred on 2012-12-29
Boot-Repair should work for grub and get you started, but if new partitions you have all new UUIDs. You will also have to manually update fstab and maybe a few other settings. 

Windows may also need repairs from a Windows repairCD as it has detailed info in the PBR that may have changed. Plus Windows hides serial numbers in MBR or if using DRM in the same area that grub writes core.img between MBR and first partition. :)

Grub remembers what hard drive to reinstall on major updates. Not sure if just a repair updates that or not, but dpkg will. You can just run after booting.

       #To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

    #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

            more /var/cache/debconf/config.dat  | grep /dev/disk
UUID in grub, fstab & maybe a few other places?

if you recreate a swap partition don't forget to update /etc/initramfs-tools/conf.d/resume with the new uuid
more /etc/initramfs-tools/conf.d/resume

Why I prefer a clean install, but that also has some hassles.

---

### Post by tedrogers on 2012-12-29
Thank you. I was beginning to think that nobody cared. :o

I will try my best and do the fstab command you mention, as well as the win repair etc.

If I'm back (which is likely to be honest) then you know I've got issues.

Sometimes it seems the shortcut is just as long as the long cut! :)

---

### Post by oldfred on 2012-12-29
From liveCD/flash drive you will have to mount your partition and edit fstab.

       UUID & labels
sudo blkid -o list

    
       sudo mkdir /mnt/sda3
sudo mount /dev/sda3  /mnt/sda3
gksudo gedit /mnt/sda3/etc/fstab

---

### Post by tedrogers on 2012-12-30
Hi again,

I'm getting somewhere with this now. Indeed, the Boot-Repair did fix my Grub2 and I am able to boot into Ubuntu on /sda3. I ended up using the Ubuntu Secure Remix iso for this, and it was pretty straightforward.

I have done most of the commands you suggested, except this one:

```
more /var/cache/debconf/config.dat | grep /dev/disk
UUID in grub, fstab & maybe a few other places?
```

I'm afraid you've lost me a little here on this (above).

The output of "more /var/cache/debconf/config.dat | grep /dev/disk" produces:

```
Value: /dev/disk/by-id/ata-Samsung_SSD_840_Series_S14GNEACA38632P
 RAW_CHOICES = /dev/disk/by-id/ata-Samsung_SSD_840_Series_S14GNEACA38632P, /dev/disk/by-id/ata-Samsung_SSD_840_Series_S14GNEACA38632P-part3
```

What, if anything, should I do with this information? What 'other places' could there be where I might need to update the UUIDs? Presumably the UUID update as been performed correctly in Grub2, else I would not be able to boot? Correct???

I edited my fstab in /etc/fstab and the only UUID (as checked with "sudo blkid -o list") that was incorrect was the swap partition on /sda2. I guess this is why when I look in System Monitor, my tux box reports that the swap is "unavailable". We will see if this has become available when I have rebooted - which, incidentaly, is lightnig quick now with this SSD installed! :)

The other issue I have now is that Win7 won't boot, claiming that the MBR is broken and that I should put my install CD in to fix it. I am yet to try this, because I want my tuxbox working great first. I only use Win7 when I need to do work in Office etc. I'd prefer a solution from within Ubuntu if possible to fixing my Win7 partition on /sda1. I just have a sneaky feeling that running the MS solution to fix Win7 will break my beloved Ubuntu!!

Thanks for your help with this so far...it's been really great and informative. I've learned so much, with much much more to learn in future.

Thanks.

== Update ==

Yes, the UUID change for the swap on /sda2 did fix it. The system monitor now shows my swap as active. :)

---

### Post by Cheesemill on 2012-12-30
> **tedrogers said:**
> Trouble is I have not cloned the MBR with Grub2 loader (for obvious reasons, the main one being that the MBR is device/HD specific, and that copying an MBR from one drive to another could spell serious trouble!)
Are you sure about this?

I've cloned entire drives including the MBR countless times and never had any issues at all, on both Linux and Windows systems.
The MBR *isn't* device specific.

---

### Post by oldfred on 2012-12-30
Windows MBR's are very generic. All they do is look for a partition with the boot flag and jump to it.
Grub MBR's may be a bit more specific in that they will look for the rest of grub in a specific place, usually using core.img which should also be cloned as it is in the sectors just after MBR. If entire drive is cloned then it should work.
But generally it is just easier to reinstall grub even when partitions are cloned.

I was adding notes to myself that other places may have UUIDs. I have not found all of them yet as far as I know, but if system is working then you should be ok.

Windows has very specific info in PBR. That includes PBR start sector & size and which boot loader to use. If anything has changed it will need chkdsk at the minimum, and maybe other repairs. If you run the auto repair from the Windows repair console, you have to run it 3 times, but one of its fixes is to restore the Windows boot loader to the MBR. That is a good way to prove that Windows does work on its own, but then you have to reinstall grub to the MBR and run sudo update-grub to add Windows to the grub menu.

       How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

---

### Post by tedrogers on 2012-12-30
Well, to be honest I just read elsewhere on the web that MBR cloning could problematic on drives of different sizes, I.e. heads, sectors etc.

My next question is probably not for this forum, as I now have Windows Is Not Genuine blue screen issue. I cannot get into the system past the login...except to ctrl+alt+del in order to shutdown. Already run the Win install DVD to repair, which is how I was able to boot into Win in the first place. Any ideas?

---

### Post by oldfred on 2012-12-30
There are two parts to MBR, boot code and partition table. If a clone partition table should be the same. But if copying full MBR back from another drive with different partition table then you may destroy drive, or have to attempt repairs with testdisk.
Why best just to reinstall grub.

When I installed new motherboard & video card, my XP had to be registered again with Microsoft. With my XP screen the login to Microsoft was under the error screen and it took me a while to find it.

---

### Post by tedrogers on 2012-12-31
Thanks for all the additional information here about MBR's, I always learn a lot from you good people. :)

I just thought I'd finish off this thread by explaining how I solved the Windows Blue Screen Not Genuine message.

It turns out that the problem was because I pre-allocated and built partitions before the cloning process on the new SSD. For some reason, and I don't know why, the new cloned device was allocated to F: instead of C: when it was cloned. Apparently, simply by not allocating a partition and instructing cloning software to use unpartinioned space avoids this problem, but that seems counter-intuitive to me.

Anyway, the problem can be fixed afterwards by first checking your drive allocation (ctrl+alt+del, then into Task Manager, then run cmd). Mine said F:, instead of the usual C:

Then getting into REGEDIT (ctrl+alt+del, then into Task Manager, then run regedit), and going to this key in the registry:

```
HKEY_LOCAL_MACHINE\SYSTEM\MountedDevices
```

For me, find the C: key (near the bottom), rename it to something else unusued (I used Z:). Then going to the F: and renaming it to C:, and finally rename the Z: to F:

Rebooted and everything worked fine. No key issues. All authenticated, etc.

I hope this helps someone else out in future.

Thanks and a happy new year to all. :)

---

