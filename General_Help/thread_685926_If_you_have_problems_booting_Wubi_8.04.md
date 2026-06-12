---
title: "If you have problems booting Wubi 8.04"
date: 2008-02-02
forum: General Help
---

### Post by ago on 2008-02-02
If you installed Wubi on a drive different from the first one, you will probably see an error like this:

[img]http://ubuntuforums.org/attachment.php?attachmentid=58348&d=1201943682[/img]

Do the following:

1) Press esc at the countdown after you select "Ubuntu"
2) Press "e" to edit the first menu entry
3) Press "e" to edit the line starting with "root (hd0,0)/ubuntu/disks"
4) You have to change the 2 numbers in there. The first number is the disk number -1, the second is the partition number -1. Change them to point to the disk/partition where you installed Wubi. If you installed Wubi on the third partition of the first harddisk, for instance, you will have to enter "root (hd0,2)/ubuntu/disks"
5) Press enter to confirm and "b" to boot

You should now be able to boot into Ubuntu. To make the above changes permanent. Open a terminal and type

sudo gedit /boot/grub/menu.lst

Edit (0,0) as explained above in the groot line, so that it points to the correct device. For sda2 that would be:

## default grub root device
## e.g. groot=(hd0,0)
# groot=(**hd0,1**)/ubuntu/disks


Save and run the following command:

sudo update-grub

A bug has been opened to address the issue: [https://bugs.launchpad.net/wubi/+bug/188460](https://bugs.launchpad.net/wubi/+bug/188460)
It will hopefully be fixed in coming releases

---

### Post by ago on 2008-02-05
If the above is not your problem but you still end up in some sort of a black screen, press esc at the countdown after you select "Ubuntu". You should see a menu with more boot options, try them out.

---

### Post by ago on 2008-02-05
If that still does not work try to run "chckdsk /r" in windows within the drive where you installed wubi.

---

### Post by ago on 2008-02-05
If you do not see a boot entry for Ubuntu at all, please make sure you have appropriate permissions.

The relevant file is C:\boot.ini for XP (note that the file is usually hidden). You should see a line such as: C:\wubildr.mbr = "Ubuntu-Linux"


For Vista you can use EasyBCD a nice utility that allows you to see/edit your boot menu.
You can also try to access boot menu from control panel > system > advanced > startup and recovery.

---

### Post by ago on 2008-02-05
If you can install and reboot, and after ~30 seconds you end up in a black screen without command line, chances are that your video driver is wrong.

Press ctrl+alt+f2 to get a shell, login and type:

sudo dpkg-reconfigure xserver-xorg

Select the Vesa driver (a low res driver that works in most cases) and leave the other options as they are. You should now be able to reboot into Ubuntu from there you can install/configure your video card driver.

---

### Post by ago on 2008-02-05
If none of the above methods work, feel free to post in the forum. It helps if you can give as much details as possible. To grab the logs, do the following:

Press esc at the countdown, select verbose mode, then look at the logs in: 

/*log 
/tmp/*log 
/var/log/* 
/var/log/installer*

You can use

grep -i err FILENAME
grep -i fail FILENAME

to display errors, or 

more FILENAME

to display the whole file (you scroll with shift pgup/pgdown, exit with q).

Ideally you can try to mount your windows partition and copy the logs there:

mkdir -p /tmpmnt
mount -t ntfs /dev/sda1 /tmpmnt
mkdir -p /tmpmnt/wubilogs
cp FILENAME /tmpmnt/wubilogs
#repeat the above for any log file in the above directories

Replace sda1 with the appropriate windows partition (/dev/sd + a=disk number + 1=partition number). 

You should now see the logs in C:\wubilogs. Zip them and post them in the wubi forum.
__________________

---

### Post by ago on 2008-02-15
For new versions of Wubi 412+, they require a new ISO with appropriate patches, but that has not been released yet.

As a workaround, when you reboot the first time you need to edit the boot option (see above) and change "iso-scan/filename=/ubuntu/..." -> "find_iso=/ubuntu/...". You can do that "on the fly" by pressing "esc" and then "e" at boot, or you can edit /ubuntu/install/boot/grub/menu.lst BEFORE booting.

The first post also applies, so you might have to change groot/root AFTER installation (second reboot), this time in /ubuntu/disks/boot/grub/menu.lst. See above for details.

All that should hopefully become unnecessary once the new ISO is released.

---

### Post by korvics on 2008-09-14
> **ago said:**
> If you can install and reboot, and after ~30 seconds you end up in a black screen without command line, chances are that your video driver is wrong.

Press ctrl+alt+f2 to get a shell, login and type:

sudo dpkg-reconfigure xserver-xorg

Select the Vesa driver (a low res driver that works in most cases) and leave the other options as they are. You should now be able to reboot into Ubuntu from there you can install/configure your video card driver.

After I type sudo dpkg-reconfigure xserver-xorg, I get a window which asks me whether I want to use kernel famebuffer device interface to communicate with the video hardware. Whether I pick 'yes' or 'no' does not matter, because next it asks me to autodetect the keyboard layout. Then then it aks what XKB rule set I should use, then what keyboard type I have etc. I do not understand how I am supposed to select the VESA driver. PLEASE HELP I'm a newby to ubuntu and this first experience is rather frustrating. 

Thanx

---

