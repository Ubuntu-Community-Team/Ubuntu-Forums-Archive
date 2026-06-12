---
title: "Wubi on Vista.. Cant Boot anything!"
date: 2007-08-10
forum: General Help
---

### Post by aktiwers on 2007-08-10
Hi all,

Okay here is the story.

My sister has a HP Pavilion laptop with Vista. I wanted to setup a dualboot with Ubuntu for her to try out.

I Installed Ubuntu using Wubi, installed all apps and drivers she needed, and rebooted.

Now Vista gives me some strange Boot error, and I am not able to boot into either Vista nor Ubuntu :(

It seams like Vista bootloader is damaged or something. Any Ideas how to fix this?

I tried with Ubuntu Live CD, but it wont even boot. Gives me some kind of sh/.. Error
Its the same error I get as this one: [http://ubuntuforums.org/showthread.php?t=522572](http://ubuntuforums.org/showthread.php?t=522572)

Also tried Vista's bcdedit.exe but without luck. I

I dont have a Vista DVD,  I only have some (useless) hp recovery CD's that I think I tried all options with.

Anyone please help! 
Thanks!

---

### Post by ago on 2007-08-10
Try to run chkdsk /r possibly from a CD.
[http://support.microsoft.com/kb/315265](http://support.microsoft.com/kb/315265)

should  be +/- the same on vista

---

### Post by dougfractal on 2007-08-10
You need to set the bios to boot from CDROM

   1.      Turn on or restart the computer.
   2.      While the display is blank, press the F10 key to enter the BIOS settings menu.
   3.      Use the right and left arrow keys to select the Advanced tab.
   4.      Use the up and down arrow keys to select Boot Order.
   5.      Follow the on-screen instructions to change the boot order.


from [http://h10025.www1.hp.com/ewfrf/wc/fastFaqLiteDocument?lc=en&cc=us&product=18703&dlc=en&docname=c00364979](http://h10025.www1.hp.com/ewfrf/wc/fastFaqLiteDocument?lc=en&cc=us&product=18703&dlc=en&docname=c00364979)
> What is the boot order?
When the notebook starts the system BIOS begins to check a pre-determined list of drives and devices that may contain an operating system such as Windows. The computer can boot an operating system from a hard drive, floppy drive, CD or DVD optical drive, USB storage device or a network. The order in which the devices are checked is configurable through the BIOS setup menu.
What is the default boot order?
The default settings for the notebooks boot order are configured in the factory. The following list is the default boot order for HP notebook PCs:

   1.
      Floppy diskette drive
   2.
      Optical drive (DVD, CD-ROM)
   3.
      Hard drive
   4.
      USB device
   5.
      Network adapter

	NOTE: 	An "operating system not found" error may appear if a floppy disk or an optical disk is inserted into the computer that does not contain an operating system. Remove the disk and restart the computer if you experience this error.
Configuring the boot order
	NOTE: 	BIOS configurations vary depending on the notebook PC. For further information on a specific notebook PC, view the documentation provided with the notebook or visit [www.hp.com](www.hp.com) . The BIOS settings are generally found in the Maintenance and Service Guide.
The following steps are for most HP Pavilion and Compaq Presario Notebook PCs. The boot order can be configured on the Advanced tab in the BIOS settings menu. The steps to modify the boot order may vary depending on the model of your computer. On most HP notebooks the boot order can be configured using the following steps:

   1.
      Turn on or restart the computer.
   2.
      While the display is blank, press the F10 key to enter the BIOS settings menu.
      	NOTE: 	Some notebook PCs use the F2 or F6 key
   3.
      Use the right and left arrow keys to select the Advanced tab.
   4.
      Use the up and down arrow keys to select Boot Order.
   5.
      Follow the on-screen instructions to change the boot order.

Reset the boot order to the default settings
Use the following steps to reset the boot order to the default settings:

   1.
      Turn on or restart the computer.
   2.
      While the display is blank, press the F10 key to enter the BIOS settings menu.
   3.
      Press the F9 key to reset the BIOS to default settings.
   4.
      Press the F10 to save the changes and exit the BIOS settings menu.

---

### Post by dougfractal on 2007-08-10
Here the fix, I'll try and make it easier.

from [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
> How can I access my Wubi install and repair my install if it won't boot?

Boot the Ubuntu Desktop CD (preferably 7.04 or newer), or another LiveCD, and create mountpoints:

sudo mkdir /media/windows
sudo mkdir /media/wubi

With the livecd's kernel-based ntfs driver, you'll only be able to get read-only access, so it is recommended to install the read-write ntfs-3g driver (you'll need a ubuntu 7.04 livecd to do this, though, the earlier versions don't have ntfs-3g in the repos):

sudo apt-get update
sudo apt-get install ntfs-3g

Then, assuming that your Windows drive is /dev/sda1 (adjust line accordingly, you can use sudo fdisk -l to find it out; see whichever one says HPFS/NTFS on the type line), mount the partition using ntfs-3g:

sudo ntfs-3g /dev/sda1 /media/windows

Before mounting the virtual disks, you'll want to check to see if the filesystems aren't corrupted or anything:

sudo fsck /media/windows/wubi/disks/system.virtual.disk
sudo fsck /media/windows/wubi/disks/home.virtual.disk

Then mount the virtual disks, once the filesystems have been checked and repaired:

sudo mount -o loop /media/windows/wubi/disks/system.virtual.disk /media/wubi
sudo mount -o loop /media/windows/wubi/disks/home.virtual.disk /media/wubi/home

Now you'll be able to access your wubi filesystem in /media/wubi read-write; your home dir will be in /media/wubi/home, and /media/wubi for the wubi root filesystem. You'll probably need to have root access to modify some files, so to open the filemanger with root privs:

gksudo nautilus /media/wubi

Optionally, if you need to do something like an apt-get to fix something, you can chroot in:

sudo chroot /media/wubi

And just run the commands you need to repair your install from within the shell that will then spawn. Once done with recovery, exit the shell and unmount the filesystems:

sudo umount /media/wubi/home
sudo umount /media/wubi
sudo umount /media/windows

---

### Post by aktiwers on 2007-08-10
Thanks a lot doug for the long guide. Actually I was thinking about doing the same thing, but if you look at the link I posted in my first post, I cant even boot the LiveCD.

Its not because BIOS isnt set to boot the CD, because it also loads the Screen where I pick "Install Ubuntu" and starts loading.

Well I guess I just do a Format and reinstall.
But thanks a lot for the help keep it comming if you have any ideas, then I will try it out before I format. 

Thanks!

---

### Post by dougfractal on 2007-08-10
from [http://ubuntuforums.org/showthread.php?t=421588&highlight=%2Fbin%2Fsh%3A+can%27t+access+tty%3B+job+control+turned+off](http://ubuntuforums.org/showthread.php?t=421588&highlight=%2Fbin%2Fsh%3A+can%27t+access+tty%3B+job+control+turned+off)
if you are getting this error (and you have a SATA harddrive); this is the fix:
> 
At the LiveCD initial boot screen:
o Select F6 for more options
o Add the following option to the beginning of the options list:
break=top
o Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
```
modprobe piix
exit
```


should boot LiveCD normally

```
sudo fdisk -l
```
see whichever one says HPFS/NTFS on the type line
and then **edit** the export WINDOWS="**sdaX**"
**This is an "sdXX" fix only not "hdXX"**


# Open a terminal (Applications->Accessories->Terminal)
# You must now mount the installed partitions by copy/paste the following ```

#Then, **assuming that your Windows drive is /dev/sda1** (adjust line accordingly, you can use sudo fdisk -l to find it out; 
#see whichever one says HPFS/NTFS on the type line), mount the partition using ntfs-3g:[B]
export WINDOWS="sda1"[/B]
sudo mkdir /media/windows
sudo mkdir /media/wubi

sudo apt-get update
sudo apt-get install ntfs-3g

sudo ntfs-3g /dev/$WINDOWS /media/windows

#Before mounting the virtual disks, you'll want to check to see if the filesystems aren't corrupted or anything:

sudo fsck /media/windows/wubi/disks/system.virtual.disk
sudo fsck /media/windows/wubi/disks/home.virtual.disk

#Then mount the virtual disks, once the filesystems have been checked and repaired:

sudo mount -o loop /media/windows/wubi/disks/system.virtual.disk /media/wubi
sudo mount -o loop /media/windows/wubi/disks/home.virtual.disk /media/wubi/home

sudo chroot /media/wubi

# You will now be in a 'chroot' command prompt for your new ubuntu system (be careful here, you are editing with root access!)
# You must edit the /etc/initramfs-tools/modules file; adding a line with the word: piix

echo piix >> /etc/initramfs-tools/modules

#o After modifying the file you must update the system with the command
update-initramfs -u

#o When complete, type 'exit' to exit the chroot env; you can now close the Terminal and reset your system.
```

---

