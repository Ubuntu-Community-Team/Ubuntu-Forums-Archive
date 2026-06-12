---
title: "How do you get USB drives to work with virtualbox windows vista?"
date: 2008-05-30
forum: General Help
---

### Post by Josh08 on 2008-05-30
Hello,

Ive just finished installing Windows Vista on VirtualBox. When i plug a usb device in, nothing happens. Ive tryed this from what i found from another website:

> Open a terminal and type

sudo gedit /etc/init.d/mountdevsubfs.sh

Go to the lines as shown below:

#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs «» /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb

Uncomment the last 4 lines and make it look like below:

#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs «» /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

Close and restart virtualbox. You should see the USB options in the settings. You can add the devices you want. I have edited and added this information to the Virtualbox installation tips I wrote few months back.

But after trying that i click onto the settings>USB and my USB drives did show up on the virtualbox settings so i added my flash disk and other devices but everytime i run my virtual machine now this error appears:

> 

**Failed to attach the USB device USB2.0 Flash Disk to the virtual machine Josh's Vista.**

Not permitted to open the USB device, check usbfs options.


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}

 

I'm confused... anyone had the same problem? :confused:

---

### Post by sdennie on 2008-05-30
If it's only usb disks that you want to be able to access, you could just let Ubuntu mount them and then use Devices->Shared Folders in VirtualBox to share them.  That will make them appear as network drives within the VM.

---

### Post by Josh08 on 2008-05-30
Thanks for the reply, i know how to setup the share folders but could you explain to me how to mount the drive, i'm kinda new to ubuntu.. :) Is it something i process in the terminal?

thanks, Josh.

---

### Post by sdennie on 2008-05-30
Normally, if you simply stick a usb disk into your machine, a nautilus window will popup with the contents of that drive (unless you've turned that off).  You should be able to simply note the name of that disk and share it to VirtualBox.  Of course, I'm not sure if those names are retained across remounts and so it may actually be easier to figure out your USB problem if you regularly need to access USB disks from the VM (however, I have no idea how to so).

Edit:
If a nautilus windows doesn't magically popup, look in /media.  The disk will likely be mounted there.

---

### Post by TenPlus1 on 2008-05-30
Here is my VirtualBox guide to install and get USB working:

Once VirtualBox is installed, run this command to add vb into the user privelages:

sudo usermod -G vboxusers -a <username>


Check USB Support:

add the group:
sudo groupadd vboxusers


add usb support:
sudo groupadd usbusers
sudo gpasswd -a <yourusername> usbusers


gksu gedit /etc/udev/rules.d/40-permissions.rules


USB devices, add lines to end of file:

# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", GROUP="usbusers", MODE="0664"
SUBSYSTEM=="usb_device", MODE="0664"


sudo gedit /etc/fstab

add this line after other volumes:
none /proc/bus/usb usbfs devgid=120,devmode=664 0 0


When running Windows or whatever Os, use the VirtualBox screen menu and install guest additions so you can access seamless mode...

This will let you share files between Ubuntu and XP (or whatever), use Net use x: \\vboxsvr\<user> to map drive letter to shared files.

---

### Post by CameO73 on 2008-05-30
[This guide](http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html) worked for me.

---

### Post by Josh08 on 2008-05-30
**@TenPlus1**

Your post seemed to fix the error, but thanks to you and everyone who's posted :)

Ive seem to ran into another problem.. When i have my virtual machine running and i insert the USB first you can hear a noice what means it's connected then i hear another noice after what means like an error. When the USB is plugged into the USB port, the flash drive does not appear on the drives list.. (on vista VM)

Anyone suggestions about this?

thanks, you've been great help so far :)

---

