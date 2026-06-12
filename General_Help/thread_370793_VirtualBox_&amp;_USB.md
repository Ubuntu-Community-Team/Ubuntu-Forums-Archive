---
title: "VirtualBox &amp; USB"
date: 2007-02-26
forum: General Help
---

### Post by bob-aptllc on 2007-02-26
I am running Edgy with Win 2000 as a guest. At first, my USB flash drive was not recognized by the guest, but now it is displayed in My Computer.

I did the following:
- Installed guest OS
- Create a group called "usbfs" and added myself to it.
- sudo gedit /etc/fstab
- Pasted in:
# 1002 is the USB group ID
none /proc/bus/usb usbfs devgid=1002,devmode=664 0 0
- Changed the group ID according to the ID for the new group "usbfs".
- VBoxManage list usbhost
- Used the output to set up the filter for my USB device in VirtualBox.
- Rebooted

Because other posts said that VirtualBox won't recognize my USB device if it is still mounted by Ubuntu, I right click on the device and "Eject" it before starting the guest, although it is still physically in the slot. When I start the guest, it displays the icon, but when I click on the icon, the perpetual hourglass appears and the guest is hung. If I start the guest, then plug the device into the slot, the device's light comes on, I click on the icon in "My Computer", then the device's light goes out and the hourglass appears until I close the app. Please help!

EDIT: Please see my update below.

---

### Post by Brunellus on 2007-02-27
I'm moving this to general support.

---

### Post by bob-aptllc on 2007-02-27
Thanks, Brunellus!

Here's an update on my VirtualBox (VB) USB situation. I had other issues and did a fresh install of Edgy. Now VB doesn't lock up when my flash drive is in, but VB does not recognize my USB flash drive at all. 

I insert the flash drive into the USB slot before I start VB or the guest, either "eject" or umount it, but when I start the guest VB doesn't recognize it. If I insert the drive while the guest is running, then Ubuntu recognizes it and the VM does not. The only visible difference between ejecting and umounting is that when ejecting, the drive's light is off, and when umounted the light stays on. Either way the VM doesn't recognize the flash drive. 

Any suggestions? Any help would sure be appreciated! :(

---

### Post by bob-aptllc on 2007-03-26
Here is a good workaround for VirtualBox not recognizing USB drives and peripherals:  [http://www.virtualbox.org/discussion/1/449#-1](http://www.virtualbox.org/discussion/1/449#-1). This approach is to not use VirtualBox's filters to mount the USB in the guest, but to use SMB (Samba) in Linux to communicate the already mounted USB device to the (Windows) guest. I was very surprised at how easy it is to set up Samba in Ubuntu! Just right-click to share the folder and not much more. Please see the link for more. :)

---

