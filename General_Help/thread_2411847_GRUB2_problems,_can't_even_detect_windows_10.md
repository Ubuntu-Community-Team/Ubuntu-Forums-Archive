---
title: "GRUB2 problems, can't even detect windows 10"
date: 2019-02-04
forum: General Help
---

### Post by vegard1992 on 2019-02-04
GRUB2 works just fine; I can boot into Ubuntu. I can not however get back into my Windows 10! It was working fine prior to installing Ubuntu.

I've tried every which way;
 * a windows recovery drive, every option
 * boot-repair, a variety of options
 * rescatux, a variety of options
 * mounting my windows partition and running grub-update
 * adding a manual entry to 40_custom (this never succeeds; i always get some odd error -- where reverting to the default file sometimes still spits out an error, and i have to reinstall grub entirely. currently even that did not work, neither did removing and creating a new file, neither did anything! ive tried many different entries as well!)
 * i tried uninstalling grub and using refind, and messing around with it a bit. this did not detect windows either.
 * tried messing around with "bios settings"; secure boot and fast boot are disabled
 * i am not entirely sure if fast boot is disabled on my windows, i think maybe not. but i did shut it down the last time i used it (although, i guess this is the point of fast boot? that even if you shut down it "hibernates"). i dont know enough here; didnt evne know it was a thing before it was a problem.
 * a bit of this and that, but these are the main strokes

This is ridiculous, because I can mount my windows partition and access my windows files; its right there! I've been at this for a solid 8 hours, and I'm out of ideas. Nothing works as advertised, and I'm no closer to getting back into Windows than I was when I started.

Thank you for reading. :P

---

### Post by ajgreeny on 2019-02-04
Did you install Ubuntu in UEFI mode or BIOS?

It will be best to see exactly where you are at present so go to **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 

**Do not run the default repair just yet** but simply copy back here the **pastebin** link you get which will show us a lot more about your system.

---

### Post by vegard1992 on 2019-02-04
oops, i ran it! here is the output currently [http://paste.ubuntu.com/p/kGbDtwM4T7/](http://paste.ubuntu.com/p/kGbDtwM4T7/)

edit: running gdisk it tells me my partition tables are currently MBR, it also gives a warning that theres "overlap"
edit: ubuntu is not on an EFI partition, it is EXT4

---

### Post by vegard1992 on 2019-02-04
i got further now! something i did made options to boot windows appear. considering it is the default option, which i specified with boot-repair, im assuming thats what did it.
windows gives me a message however that my boot configuration files are broken. i tried with a windows recovery usb and ran bootrec /fixmbr & bootrec /rebuildbcd and that did not help.

i also installed grub-customizer, and the script for booting windows reads as follows; 
```

search --fs-uuid --no-floppy --set=root 7EB8-B2AE
chainloader (${root})/EFI/Boot/bkpbootx64.efi


```

---

### Post by oldfred on 2019-02-04
Script does not show all the details on the new NVMe drives.
But Windows only installs in BIOS boot mode with MBR (msdos) partitioned drives and only with UEFI boot mode on gpt partitioned drives.
I would expect a new drive to use the new gpt partitioning and UEFI, not the old MBR.
Did you install Windows yourself and not choose the UEFI boot mode when installing?

You show Windows UEFI boot files in sda, which looks like your flash drive. That seems very strange.

Post this:
sudo gdisk -l /dev/nvme0n1

---

### Post by vegard1992 on 2019-02-04
for nvme0n1 [https://pastebin.com/nWKpW8KS](https://pastebin.com/nWKpW8KS)
for nvme0n1p2 which is the partition with windows [https://pastebin.com/RpTKUqhS](https://pastebin.com/RpTKUqhS)

---

### Post by vegard1992 on 2019-02-04
windows has a reinstall option where you can keep your files. im going to make a windows usb installer and see if that wont help. im guessing it will wreck grub and stuff though? but ill just have to try, its more important i get my windows back up and running right now.

i thought i might clone my ubuntu partition to an ssd, is this possible? i may have to resize it slightly with gparted though



the windows error im getting upon booting is
```

(something like this)
boot configuration file error 
/EFI/Microsoft/Boot/BCD missing or broken

error code: 0xc000000f

```
ive tried a lot more fixes using my windows recovery usb, none of which were succesful

---

### Post by oldfred on 2019-02-04
Did you somehow force a BIOS/MBR install over gpt?
Windows is known to not really convert gpt correctly to MBR. It leaves the backup gpt partition table and that almost always creates issues with Linux tools. That also may be the overlap issue as partition may be into backup gpt table, even if not now used.

Do you know if Windows was UEFI or BIOS? And vendors are required to install in UEFI/gpt mode, but users can install or reinstall in BIOS/MBR.
Windows only boots in UEFI mode from gpt drives.

---

### Post by vegard1992 on 2019-02-05
i installed windows myself. so it may be MBR. i did a test and some tools reported MBR. 

all the meddling i did probably didnt help either, if windows ever did boot, it definitely does not now.

is it possible i could create a gparted bootable usb, and use the partition table fix in gparted? would that help?

---

### Post by oldfred on 2019-02-05
I usually just use the gparted on the Ubuntu live installer.
But the gparted ISO is often one or two versions newer. 

I use grub to directly boot ISO, so I use one flash drive for many ISO, rather than multiple flash drives.
Back when using DVDs I made all the recovery software as new DVD before reinstalling (as well as backups). But went thru so many DVDs, I converted to flash drives. But when flash drives became larger, I did not want to dedicate one to just one application.

Unless you happen to have some data at very end of drive, you can generally just delete partition and then recreate slightly smaller. Good backup still required.

       repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
last partition overlaps backup partition table
[http://ubuntuforums.org/showthread.php?t=1956173](http://ubuntuforums.org/showthread.php?t=1956173)
Check start & end, delete and recreate without overlap. Backup vital just in case.

---

### Post by vegard1992 on 2019-02-05
oh boy, im shut out of ubuntu now!

it gets stuck on start screen. tries for 1.5 mins saying something like "a startup thing on somedev.device running (0s 1m30s)"

after completing and entering maintenance mode, and checking "journalctl -xb" its saying the "waiting for somedev.device timed out"

the device does not look like one that ubuntu is on, so i guess grub points to the correct device, but ubuntu internally thinks its another device?

i did some meddling with devices to get my USB stick recognized by ubuntu, i think thats where i may have gone wrong? how to i set my device.

i tried "sudo grub-install /dev/nvmen1p4" which should be correct, then updated grub. that didnt help. kind of makes sense though, since this only deals with grub
and if grub was pointing in the wrong place, i wouldnt even get into ubuntu.

---

### Post by vegard1992 on 2019-02-05
i also tried to reinstall windows with the option of keeping my files intact, but it wouldnt let me, saying i already had to have windows booted!

my computer is dying piece by piece, and every action i take is just another stab right to its heart :KS

---

### Post by vegard1992 on 2019-02-05
okay. fixed ubuntu boot error! WHEW. haha

i had added an entry in my fstab file, which was supposed to mount my usb somehow. just had to delete that entry.

edit: 

managed to bomb everything and get shut out, but recovered my ubuntu installation! \o

back to square one!

---

### Post by vegard1992 on 2019-02-05
SOLVED

i don't know exactly what fixed it. but i think its something like this;

these first steps are potentially optional - 
1. boot into gparted usb media
(at this point i managed to reformat my drive by trying to create a new partition table - DONT do this!!)
2. while recovering however, i may have managed to fix an overlap error by reducing the length of my partition table or something. i do not recall what tool i used unforunately! something like gdisk though i think?

however, unless the above edited the actual windows and ubuntu partitions, it probably did nothing as i;
3. wiped all boot partitions
i dont know if the following REQUIRES you to have an EFI installation of windows, and ubuntu, or if it will fix everything regardless. also i messed around with some GPT stuff when i managed to wipe everything with gparted, again, not sure if this has anything to do with anything.
4. out of the newly unassigned memory i created one EFI partition
5. i then followed this, approximately [https://askubuntu.com/questions/831216/how-can-i-reinstall-grub-to-the-efi-partition](https://askubuntu.com/questions/831216/how-can-i-reinstall-grub-to-the-efi-partition)
6. finally i edited the UUID in my /etc/fstab of my ubuntu installation to match the new EFI partition UUID

i could now boot into ubuntu

to fix windows;
7. booted up a windows installation media (a recovery tool, which can be created by typing "recovery tool" in cortana, could probably be used)
8. selected advanced troubleshooting, and went into the console
9. apparently many people can fix their boot problems at this point by running bootrec /fixboot, however this returned "access denied" for me
10. what i needed to do was create a label for both EFI drive and windows drive using DISKPART and run this command
11. "bcdboot N:\windows /s M:" where N is windows drive label and M is EFI drive label

i could now boot into windows

not quite done yet though!
this breaks grub!

so after disabling fast startup in windows, i rebooted my ubuntu live usb

12. after booting to ubuntu live usb
13. download boot-repair and run recommended repair
14. if everything succeeds, you can now reboot, and hopefully you can start both windows and ubuntu from grub!

voila!

---

### Post by ajgreeny on 2019-02-06
Brilliant!! 

Even though I do not completely understand the processes you went through to get back up and running, not having used Windows properly for 14 years, I am delighted you got things working again.
Please can you now mark this as SOLVED from the Thread Tools menu up-top if this really is now solved to your satisfaction. 

It is a great help to users searching the forum.

---

