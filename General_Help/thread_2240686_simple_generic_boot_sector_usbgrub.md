---
title: "simple generic boot sector? usb/grub"
date: 2014-08-21
forum: General Help
---

### Post by Sandgoose on 2014-08-21
I have one of those usb sticks that sit almost flush to the laptop and are intended for permanent storage, the problem is on boot the laptop sees this device tries to boot it then proceeds to hang when it finds no boot sector meaning I have to restart hit esc and tell the bios to boot from the hdd every time.

is it possible to tell grub to install the boot sector to 2 different drives and have this configuration update when software updates are installed?

or is there any easy way to get a simple bootloader into the usb that will redirect to the first harddrive 

I have tried searching for a solution but im not really sure what I am looking for, I had considered reinstalling the os and telling it to stick the master boot on the usb during install as it always seems to boot usb but that would render the device unbootable if it were removed at some point.

thanks

---

### Post by ajgreeny on 2014-08-21
I suspect you could install grub on that USB disk, as well as the hard disk, without too much difficulty with command ```
sudo grub-install /dev/sdx
``` where sdx is the USB disk name.  What I am unsure of is how exactly this grub can be forced to look to your hard disk for all the configuration files needed for grub to work, and if it will update automatically whenever there is a new kernel or even a new distro is added to your machine.

---

### Post by yancek on 2014-08-21
Why can you not just set the internal hard drive to first boot priority in the BIOS?

---

### Post by Sandgoose on 2014-08-21
@yancek laptop runs seabios as far as I know there are no configuration settings, if it detects a removal device while booting it tries to boot from it ;)

@yancek I suspect this will work thanks although I curently have the device setup as fat and it gave an error, wondering if I change it to ext will it behave the same (removable storage from desktop icon) I probably should have just set it up as my home dir but didnt own the device when I did the initial install.

thanks

---

