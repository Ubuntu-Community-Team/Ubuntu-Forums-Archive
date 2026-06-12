---
title: "Can I get a Safe Hardware Removal icon in the system tray?"
date: 2007-09-22
forum: General Help
---

### Post by MegaSvensk on 2007-09-22
Is there anyway I can get an icon in the system tray that I can use to disconnect devices? I find that feature to be very convenient in Windows.

Also, I think that my San Disk memory stick might not be disconnecting properly when I dismount the drive because on Windows, the red light on the stick is turned off when I've disconnected it in "Safe Hardware Removal", but in Ubuntu, the light stays on. Is dismounting the proper way of removing external drives in Ubuntu or are you supposed to do something else?

---

### Post by GadgetsGuy on 2007-09-22
I may stand to be corrected, but as I understand it, Linux does not need a 'safe removal' option ...

Unmounting the device, and then unplugging the device from your computer will remove the device  ...

Linux is a different architecture than windows, and does not need functions such as 'safely remove device' or specific uninstall procedures for programs ...

The same way you can uninstall programs in Linux by simply deleting the program files, you can also remove USB devices by simply unmounting/removing the device.

---

### Post by 67GTA on 2007-09-22
Just right click on the icon and click "unmount". Then disconnect your device. That is all that is required.

---

### Post by kostkon on 2007-09-22
Indeed, just right click on the device icon and select the *Eject* option. That's the way you do safe removal of a usb device in Linux.

---

### Post by dcstar on 2007-09-22
> **kostkon said:**
> Indeed, just right click on the device icon and select the *Eject* option. That's the way you do safe removal of a usb device in Linux.

And if there are any problems Linux will let you know, it assumes the users do not want to be treated like idiots and have to be told when there are **no **problems.......

---

### Post by 67GTA on 2007-09-23
I am testing Kubuntu 7.10, and it actually has a "safely remove" option when I right click on my mounted SD camera card.

---

### Post by olddave on 2007-09-28
What happens if this is a device such as an adapter that does not have a desktop icon?

---

### Post by isecore on 2007-09-30
> **olddave said:**
> What happens if this is a device such as an adapter that does not have a desktop icon?

If it's not a drive of some kind it doesn't need to be unmounted. The reason for unmounting is to prevent loss of data that might/should've been written to the drive - the same reason the "safe removal" exists in Windows.

Since this only applies to devices with storage there is no need for it when it comes to other devices. Just yank them out and be happy.

---

### Post by santiagoward2000 on 2007-09-30
I don't know about Gnome, but in XFCE you can add a "Mount Devices" item to the panel. It can mount or unmount connected drives.

---

### Post by olddave on 2007-10-05
Thats what we have been doing, but when I do that with the wireless usb adapter, the thing is completely fubar until we plug it into a machine and REBOOT the machine.  This is the only way we have managed to get the usb device to work on ANY machine after yanking it out.

Any clues?

---

### Post by strabes on 2007-10-05
> **MegaSvensk said:**
> Is there anyway I can get an icon in the system tray that I can use to disconnect devices? I find that feature to be very convenient in Windows.

Also, I think that my San Disk memory stick might not be disconnecting properly when I dismount the drive because on Windows, the red light on the stick is turned off when I've disconnected it in "Safe Hardware Removal", but in Ubuntu, the light stays on. Is dismounting the proper way of removing external drives in Ubuntu or are you supposed to do something else?

In Gnome, right click on empty space on the panel, click "Add to Panel..." and add the "Disk Mounter" applet. It will show all your mounted drives and media. To unmount drives, just click on them and click unmount.-

Regarding your second question, I don't think it should be much of a problem.

---

### Post by isecore on 2007-10-06
> **olddave said:**
> Thats what we have been doing, but when I do that with the wireless usb adapter, the thing is completely fubar until we plug it into a machine and REBOOT the machine.  This is the only way we have managed to get the usb device to work on ANY machine after yanking it out.

Any clues?

Sorry, then I'm fresh out of clues why it happens. Maybe a bad device? Or maybe something that doesn't quite comply to standards? But other than that I have no idea.

---

### Post by Cupcake123 on 2007-10-07
> **strabes said:**
> In Gnome, right click on empty space on the panel, click "Add to Panel..." and add the "Disk Mounter" applet. It will show all your mounted drives and media. To unmount drives, just click on them and click unmount.-

That's certainly true, but umounting is different to safely removing (or ejecting). If the GNOME desktop doesn't have the ability to safely remove/eject devices, that is (IMHO) a serious deficiency. The gnome-mount command does have an eject option, but for whatever reason Disk Mounter doesn't make use of it.

I posted a question about this the other day: [http://ubuntuforums.org/showthread.php?t=567562]("http://ubuntuforums.org/showthread.php?t=567562").

You can do e.g. "eject /dev/sda" from the command line after unmounting any partitions (and maybe using the sync command - or does unmounting automatically sync all cached data to disk?). But there doesn't appear to be any way of doing that from the desktop GUI.

For hard drives, it's very important to "eject" them, because the drive then spins down and parks its heads. Just powering off the drive will, over time, reduce its life. (When a spinning drive is powered off, the heads are parked in a "rougher" way.)

I would strongly recommend you also "eject" USB flash drives before removing. You can imagine a high-speed flash drive which has some buffer RAM to make writes appear faster. Just yanking it out might cause data to be lost, whereas ejecting would tell the drive to write its buffer to the flash ROM.

Also, ejecting should turn off any activity light on the drive. With my mobile phone, its screen says it is safe to remove after I eject it. The same will apply to an iPod etc.

---

### Post by swarup on 2007-10-17
> **olddave said:**
> Thats what we have been doing, but when I do that with the wireless usb adapter, the thing is completely fubar until we plug it into a machine and REBOOT the machine.  This is the only way we have managed to get the usb device to work on ANY machine after yanking it out.

Any clues?

Does anyone have a solution for this? I am also having the same problem. I use a Netgear USB wireless adapter. My on-line connection is great. But I can't pull the adapter out of the USB socket without the laptop freezing up. 

Because the adapter is not a storage device, so it does not seem to have the same permissions for "unmounting" as a storage device would have. Is there any sort of way to get the computer to recognize I am going to unplug the device so it will be prepared for it, and thus not freeze up when it happens? Thanks!

note: someone suggested the below to me. Does Ubuntu have any feature such as the below, or could any such applet be added?
> 
You may need to find some utility to allow device removal by hotplug, such as the Windows device manager, where you can disable a device by right clicking it's name.I don't know if Ubuntu has this option, i have never run across it in my travels in and out of the O/S. 

---

