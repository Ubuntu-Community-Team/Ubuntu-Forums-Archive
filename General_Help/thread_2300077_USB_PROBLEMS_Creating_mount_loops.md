---
title: "USB PROBLEMS Creating mount loops"
date: 2015-10-23
forum: General Help
---

### Post by rex8 on 2015-10-23
OK, so I was going to make a live USB for gparted like I have done many times using StartUp Disk creator.. I erased the whole disk and then it wouldn't boot with the image installed.. I tried multiple times and then messed with the edit partition and edit system type for my USB and messed it all up.. Now when trying to create a bootable disk, it's showing another mount point besides just the usb where the boot info must be going to.. My USB used to be called sdf1 I believe, and now it's sdba1. Fdisk is showing;  

 Device Boot      Start         End      Blocks   Id  System/dev/sdb1   *           1    30490623    15245311+  ee  GPT

and in my sys/class/block directory I have about 8 loop files, ram1 ram2 etc files and from each time I tried to make a new bootable disk. I guess it was writing it to my system and not just my usb.. When I plug my usb into a windows machine.. It can read the files, but when I try to make a live boot disk in windows it doesn't even recognize my USB anymore.. I know I messed this all up with Startup Disk Creator by messing with all of the options.. How do I remove all of these loops and make my USB bootable again? Please help before I do any more damage lol

---

### Post by sudodus on 2015-10-23
I think you can unmount the loops with

```
sudo umount /mountpoint/
```, but it is much easier to simply reboot the computer.

I suggest that you try another tool to make a live USB drive. ***What iso file*** are you trying to flash into the USB drive? Different tools might be best for different iso files.

---

### Post by rex8 on 2015-10-23
> **sudodus said:**
> I think you can unmount the loops with

```
sudo umount /mountpoint/
```, but it is much easier to simply reboot the computer.

I suggest that you try another tool to make a live USB drive. ***What iso file*** are you trying to flash into the USB drive? Different tools might be best for different iso files.




I've used unetbootin and It wont install.. Even tried with windows Image burn and it wouldn't even recognize my USB as being bootable.. Yet I can see the and move the files that are on it. I've tried gparted, mint, ubuntu 14.. 15.. windows 7 recovery.. Nothing works trust me, and I've used the iso's before... The usb was always known as sdf1 but now it is sdb1.. I know I did it messing around with the MBR and linux boot partition built into the StartUpDiskcreator options and the bootup and technical system settings. When I create an image with unetbootin I can see my usb mount and another loop mount point pop up with it until the image is done being created.

---

### Post by sudodus on 2015-10-23
OK, you have several iso files. I think the linux iso files will work, when ***cloned*** to the pendrive (unless the pendrive is damaged physically/electronically, but I don't think so).

If you [try to] make the pendrive bootable in Ubuntu, I suggest that you use [mkusb](https://help.ubuntu.com/community/mkusb). If you do it in some other linux distro, mkusb might or might not work, but mkusb-nox or mkusb-bas might work. It 'wraps a safety belt around dd'. (dd is the tool under the hood, that clones the iso file to the pendrive.)

If you [try to] make the pendrive bootable in Windows, I suggesst that you use [Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager/iso2usb), which does the corresponding task.

---

### Post by rex8 on 2015-10-23
I've made these same images with this same USB drives multiple times easily. I can make the iso from the command line and it still wont boot. I changed the settings on the  boot partition of the Usb drive itself and need to know the correct settings in Ubuntu DISKS to change it back to normal.

---

### Post by sudodus on 2015-10-23
If the partition table of the pendrive is damaged, it works with cloning, because that process overwrites the file system anyway.

But if you want to use Unetbootin or the Startup Disk Creator, you might need to wipe the first megabyte and after that create a new partition with a FAT32 file system. You can do that too with [mkusb](https://help.ubuntu.com/community/mkusb) via its wipe menu. It is easiest to use the 'bleeding edge version' [from the unstable ppa or from phillw.net](https://help.ubuntu.com/community/mkusb/gui).

---

### Post by sudodus on 2015-10-23
I think we might need to step back and ask some general questions, if there are still problems:

Is the computer running in UEFI or BIOS mode?

Can you boot another computer from the pendrive?

---

### Post by rex8 on 2015-10-23
> **sudodus said:**
> I think we might need to step back and ask some general questions, if there are still problems:

Is the computer running in UEFI or BIOS mode?

Can you boot another computer from the pendrive?


 It's bios, and it won't boot from any computer.. I've tried machines with  UEFI and BIOS Firmware... When I try to create a live usb with unetbootin for example, it copies itself here's what it said  /dev/sdb1 is mounted on /media/rex/black         Rex being my user name and black was the name of the usb.. So it's mounting itself to my HDD and also not being seen as bootable.. The usb drive was 16gb.. It always showed around 15.5 gb when empty.. now it says 16gb when it's empty.. Like I deleted a filesystem in the USB

---

### Post by sudodus on 2015-10-23
1. Please reboot the computer to get rid of the extra loop mounts.

2. Give mkusb a chance to make the pendrive working again.

Good luck :-)

---

### Post by rex8 on 2015-10-23
> **sudodus said:**
> 1. Please reboot the computer to get rid of the extra loop mounts.

2. Give mkusb a chance to make the pendrive working again.

Good luck :-)


Yeah, still no luck. My Hirens boot cd boots up fine loaded on my other usb stick. and this one still has issues.. Still don't know what caused it's mount point to change from sdf1 to sdb1 when I messed with the filesystem settings of the usb drive. Oh well, guess I will try another usb... Ive done this so many times before and Idk what I did wrong this time lol

---

### Post by sudodus on 2015-10-23
Tough luck,

If mkusb can't make the pendrive work again, I think it is damaged beyond repair.

---

