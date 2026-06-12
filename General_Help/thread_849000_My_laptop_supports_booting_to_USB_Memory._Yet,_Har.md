---
title: "My laptop supports booting to USB Memory. Yet, Hardy on external HDD - &quot;No OS Found.&quot;"
date: 2008-07-04
forum: General Help
---

### Post by Roasted on 2008-07-04
Simple as the title says. I installed Hardy with my external hard drive plugged into my desktop. It installed successfully. It's 80gb. I did 1gb swap, 20gb ext3 root, and the remainder just unallocated, figuring later I'd format it to NTFS and still have some space to use the functionality of an external hard drive.

I booted to USB Memory Device on my laptop.
It failed.
How can I fix it?



PXE-E61: Media test failure, check cable.
PXE-MOF: Exiting PXE ROM.
Operating System Not Found.


:(

---

### Post by vandorjw on 2008-07-04
Happend to me also,

I forgot to add "lilo" to the USB stick.
after that, everything was smooth sailing
> 
Notes: If your having trouble getting Ubuntu to boot, your memory stick may have a corrupted MBR. To repair the MBR of your USB device, at the terminal type **sudo apt-get install lilo** then type lilo -M /dev/sdx (replacing x with the letter of your flash device)

---

### Post by Roasted on 2008-07-04
Lilo? Is Lilo a must for USB devices, or will grub work?

I went through the typical installation. I don't see why the boot loader would have been missed...

---

### Post by vandorjw on 2008-07-04
I don't think Lilo is a must...if you want you can try
sudo apt get install grub -- and make necessary changes.

by the way..did you actually do an install to the USB?

or did you follow a guide like this?

[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

----------------
if you did a normal install...grub is very likely to be on your Hard drive... :)
boot from hard drive, and select Ubuntu....maybe that will work.

---

### Post by Roasted on 2008-07-04
I plugged in the USB external hard drive. I went into GParted and wiped it with EXT3 just to clear the drive.

Then I rebooted, Hardy Heron CD in my computer, external hard drive plugged in and turned on.

I followed a regular installation, however, I just made sure to select the external hard drive when I set up the partitions.

---

