---
title: "Gutsy + VirtualBox + USB + Windows Mobile = Code 10??"
date: 2008-01-02
forum: General Help
---

### Post by nocturnal9 on 2008-01-02
I've survived for two months as a new Ubuntu user only using searches on this forum, but I've gotten to an issue I actually need to post a question about.

I have a Windows Mobile device (an iPaq Z125 or rx1955, I'm not sure which is the model number but I don't think it matters).  On Windows I had used a piece of software to sync it to multiple Google Calendars by way of Microsoft Outlook, and having read about the Ubuntu/WM problems I figured it would be best to manage my iPaq virtually.

I have Windows XP running in a VirtualBox and have followed the instructions here:
[http://www.arsgeek.com/?p=2776](http://www.arsgeek.com/?p=2776)
To get USB set up with VirtualBox.  However, when I try plugging my iPaq in via USB, the virtual Windows recognizes it correctly as a "Windows Mobile-based device" and then a few seconds later Device Manager begins to report:

*This device cannot start. (Code 10)*

I feel like Ubuntu is not ceding enough of the USB over to VirtualBox, because it works when I dual-boot to Windows.  Anybody have any suggestions to what I could do to make this work better?

---

### Post by andymushu on 2008-01-04
i found that those hacks to get usb working with virtualbox always messed with my virtual machine, so i uninstalled the OSE (opensource edition) version of virtualbox (the one in the repositories), and went straight to virtualbox's website and got the non-opensource edition, located [here]("http://www.virtualbox.org/download/1.5.4/virtualbox_1.5.4-27034_Ubuntu_gutsy_i386.deb"). Be sure to uninstall the previous version before installing this one. Once you have this version running, simply click on the settings button for your virtualmachine and go to usb settings. Plug the device in, then click on the green plus button on the right side (this may not be exact, as this is from memory). Once you click that button, a dropdown menu should appear with your device listed. Click your device on that listing, then just hit OK on the bottom. Startup your virtual machine and that device should be automatically recognized and go straight to the vm without ubuntu touching it, giving the vm full control over it. Hope this helps.

---

### Post by freddyp on 2008-01-04
I had to make several changes to my Gutsy 71.0 configuration to get USB working with a home automation packge running in VirtualBox 1.5.2 under Windows XP.  Here's what I did:

Downloaded the current version directly from the VirtualBox site, installed, and then made the following two changes to get USB devices working in VirtualBox.

Note -- I'm running VirtualBox 1.5.2; the web site has a new 1.5.4 version.  Not sure these changes are required in 1.5.4.  I suspect they are still needed.

****************************************************

FIRST CHANGE - edits to /etc/init.d/mountdevsubfs.sh

Support for /proc/bus/usb/* was removed in Ubuntu 7.10.  Software developers will (over time) port USB calls to check /dev/bus/usb first but until then the following work-around re-enables /proc/bus/usb/devices in Ubuntu 7.10.  It appears that VirtualBox 1.5.2 still calls /proc/bus/usb/devices.

In a terminal windows execute the following:

sudo /etc/init.d/mountdevsubfs.sh

The edits involve simply removing the # (comment symbol) from the mkdir through mount lines (Code after line 40)

	#
	# Magic to make /proc/bus/usb work
	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb

Execute the script manually to enable the change before a system reboot by running the following in a terminal window:

sudo /etc/init.d/mountdevsubfs.sh start

*****************************************************

SECOND CHANGE - edits to /etc/udev/rules.d/40-permissions.rules

This provides/enables USB selection icon in VirtualBox.  In a terminal window execute the following:
 
sudo gedit /etc/udev/rules.d/40-permissions.rules

Here are the edits in the file. 

#Edited to enable USB devices on VirtualBox
#Original line commented out under #USB devices (usbfs replacement)
#added the new line

# USB devices (usbfs replacement)
#SUBSYSTEM=="usb_device",		MODE="0664"  # ORIGINAL
SUBSYSTEM=="usb_device",		MODE="0666"  # NEW LINE ENABLES USB ICON

# Now in VirtualBox select your machine, select USB controller,
# select Enable USB controller and add filter with blanks

# On the bottom of the VirtualBox window there is a icon to add USB devices
# right click and select device - to be safe you should unmount USB device
# in Ubuntu first

# ----------END OF COMMENTS -----------------------

Hope this helps!

---

### Post by irifan on 2008-01-06
Enabling USB support worked fine (you just forgot the gedit in sudo /etc/init.d/mountdevsubfs.sh)

I enabled both the USB and USB EHCI controllers (Virtualbox 1.5.4).

I connected the Windows Mobile Device and pressed Add from, selected the HTC Generic RNDS.

After rebooting XP I conected the Windwos Mobile Device again, and got the following error message:


Failed to create a proxy device for the USB device. (Error: VERR_FILE_NOT_FOUND).

Result Code: 
0x80004005
Component: Console
Interface: IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

The device manager has a Windows Mobile based Device in the Network adapter section. however it has the nast yellow !   ant Properties tells me: This device cannot start. (Code 10)

---

### Post by andymushu on 2008-01-06
i believe i solved that issue by creating a "usbfs" group under system-->administration-->users and groups. then i added myself to that, and logged out then back in. hope that works for you.

---

### Post by solitone on 2008-01-13
> **irifan said:**
> 
I enabled both the USB and USB EHCI controllers (Virtualbox 1.5.4).

I connected the Windows Mobile Device and pressed Add from, selected the HTC Generic RNDS.

After rebooting XP I conected the Windwos Mobile Device again, and got the following error message:

[FONT="Lucida Console"]Failed to create a proxy device for the USB device. (Error: VERR_FILE_NOT_FOUND).

Result Code: 
0x80004005
Component: Console
Interface: IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
[/FONT]

I have the same error when USB 2.0 (USB EHCI Controller) is enabled in VirtualBox. Nevertheless, USB works fine in the guest when USB 2.0 is disabled. Unfortunately this means that I/O is much slower - but at least it works..

Could you please tell me whether you experience the same behaviuor?

I run VBox 1.5.4 on Ubuntu 7.10.

---

