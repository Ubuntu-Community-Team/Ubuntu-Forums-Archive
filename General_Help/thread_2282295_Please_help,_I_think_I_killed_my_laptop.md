---
title: "Please help, I think I killed my laptop"
date: 2015-06-13
forum: General Help
---

### Post by jamie17 on 2015-06-13
I was running ubuntu alongside windows 8 but decided to uninstall it, so I booted into windows and deleted the Ubuntu partition and extended my windows partition back to how it was before... And it seemed fine. Until I actually turned my laptop off and back on again. 

Then I got a screen which said something like "no such partition"  and "grub rescue".. I kind of panicked so I went into the bios, and foolishly enabled fast boot thinking that it might help in some way.. But I've only made things worse. 

Now when I turn on my laptop, there's nothing on the screen at all.. It comes on, I can hear the fans etc. But the screen is just black and I can't do anything. Pressing F12 etc doesn't work anymore. 

Is there anything I can do? :(

---

### Post by jhecn on 2015-06-13
You can try to boot from a live CD if your computer still allows this.

---

### Post by jamie17 on 2015-06-13
I'm not sure how I'd go about doing it.. The screen is just black from the start and nothing i press seems to do anything..

---

### Post by ajgreeny on 2015-06-13
After installing Ubuntu the boot process was managed by grub and grub was dependent upon files and folders in your Ubuntu OS.  Those files are now gone but grub is still trying to manage the boot process and failing as it can't find them.

If you made the DVDs that are recommended by windows when you first ran that OS you can use that DVD to repair the boot process and get back the windows bootloader system, but not having used windows for many years, I can't give you more detail on how to do this.

I think it may still be possible to get a basic windows bootloader using a Ubuntu live system and installing **lilo** to that and then using a simple command to get your windows booting again, but Win 8 and machines that use UEFI may no longer work that way, so wait for more replies before trying that.
> You can install a Windows equivalent MBR to your sda drive by doing the following from your Live CD:
```
sudo apt-get install lilo
```
Ignore the warning then 
```
sudo lilo -M  /dev/sda mbr
```

Then you should be able to boot directly into Windows again if all goes well.

A google search for "restore windows 8 bootloader" may give you more options than I know of.

---

### Post by leunam12 on 2015-06-13
Insert the live DVD and turn it on and just wait a few minutes to see if it kicks in.

If it doesn't work you have to check in your computer's documentation or manufacturer's website how to access BIOS when fastboot is enabled, this varies depending on the manufacturer. For example, some Lenovos have a secondary power button that when you press it gives you the option to go to system settings. Some Toshibas will go to system settings if you press F2 while turning it on, etc. You have to find out how to do this.

Another idea: If the CMOS battery is easily accessible (you would have to remove the cover doors at the bottom of the laptop and look) pull it out and wait a few minutes and put it back in and when you turn the laptop back on it will probably tell you that you have to adjust the date and time, etc. and it will let you go to BIOS. You have to be really careful if you do this because you don't want to break anything.

Other computers will give you the option to go to BIOS if the amount of system memory changes, so if you pull a RAM stick out and start with just one, it may let you go to system settings.

When you can get to the settings disable fastboot.

---

### Post by jamie17 on 2015-06-13
Thank you so much, it's a Toshiba and holding F2 when turning it on worked. Now I can disable fastboot and at least be back to where I was before.

---

### Post by leunam12 on 2015-06-13
Attaboy! now boot from the live DVD or USB and follow the directions on the link below:

[http://www.howopensource.com/2011/08/restore-mbr-from-ubuntu-live-cd-usb/](http://www.howopensource.com/2011/08/restore-mbr-from-ubuntu-live-cd-usb/)

---

### Post by stalkingwolf on 2015-06-13
you used to be able to run the repair function for windows then run fix mbr and that would fix it but im not sure anymore.  grub repair disk might also fix it

---

