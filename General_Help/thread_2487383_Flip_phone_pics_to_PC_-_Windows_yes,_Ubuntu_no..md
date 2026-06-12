---
title: "Flip phone pics to PC - Windows yes, Ubuntu no."
date: 2023-06-02
forum: General Help
---

### Post by nowindows2 on 2023-06-02
I have a Verizon/Kyocera flip phone (not a smartphone), and I'm trying to transfer pictures from the phone to my Ubuntu Jammy Jellyfish PC.

The normal sequence with Windows is to plug the phone into the PC via usb, then click 
Phone Settings ---> USB Mode ---->, then switch from "Charge Only" to "Media device (MTP)". The images show up and I can view the media and/or drag them to the PC.  

With Ubuntu, it's sees the phone, but not the images or videos.  I can import MPEG4s and jpgs from my Canon camera no problem. It's just the phone media that it doesn't see.  Should I install gvfs-mtp via sudo apt?

I've only just switched from Windows to Linux a few weeks ago so although I did do a search, the answers are a bit above my paygrade. I did a minimal install and the only two programs I've added to JJ are Gimp and smplayer. 

Thanks.

--------------------------

Search results:

Does Linux support MTP?
MTP is primarily used in devices running the Android operating system. In this article, we'll discuss how we can mount the MTP devices under Linux. We'll cover the gvfs-mtp package, which comes with most major Linux distributions.Nov 30, 2022

How to mount MTP device Linux?
To mount or dismount from a command with gvfs-mtp use Bus and Device numbers, e.g. to mount gio mount mtp://[usb:001,007]/ and to unmount gio mount -u mtp://[usb:001,007]/ . The mounted device will be available in a directory that begins with mtp:host= and is located under /run/user/$UID/gvfs/.Mar 21, 2023

The gvfs-mtp module is designed to work solely with MTP devices. It lets us access the MTP devices through a FUSE file system.

---

### Post by TheFu on 2023-06-02
Run **dmesg -w** in a terminal, then connect the phone over USB.  Is anything seen?  If not, the the udev rule for that specific device are unknown to Linux.  I think you can add them, but I don't have time to look up exactly how or whether this is sufficient to get a working MTP connection.

**lsusb ** can show the USB device ID and you can look up online if drivers are available or necessary to use it.

Otherwise, pulling out the microSD card and accessing that directly from Linux might be the easiest answer.

---

### Post by nowindows2 on 2023-06-02
[QUOTE=TheFu;14145486]I don't have time to look up exactly how or whether this is sufficient to get a working MTP connection.

**l**/QUOTE]

I wouldn't expect you to :)

You've pointed me in the right direction and I appreciate that. I'll try your suggestions tomorrow.  Thanks!

---

