---
title: "Is there anyway to extract files from a VM when VMWARE won't load?"
date: 2007-04-21
forum: General Help
---

### Post by bankie on 2007-04-21
[So the Feisty upgrade hosed my Edgy setup.]("http://ubuntuforums.org/showthread.php?t=416989") I can start off of the Feisty LiveCD and get to my VM files but have no way to load the the VM. Is there any way that I can extract files without a working VMWARE installation?

---

### Post by codingmaster on 2007-04-21
Hello!

vmware provides some tools for Linux.

Please check:
[http://www.vmware.com/support/reference/linux/loopback_linux.html](http://www.vmware.com/support/reference/linux/loopback_linux.html)


Best regards, Georgy Berdyshev

---

### Post by Alterax on 2007-04-21
Here's something you can try:

Download a copy of some type of Live-CD linux.  The Ubuntu ISO or Knoppix work fine for this.  Change the settings for your VM to point to that ISO instead of to an actual CD-ROM.

Get the machine to boot, but QUICKLY click into the window and hit escape while it's going through the mock POST bootup sequence.  This brings up a menu of start devices.

Make it boot from the "CD-ROM" (actually the ISO, but who's counting?) and you should be able to work with your files that way.  You can get them out by opening a Samba or FTP shared folder on your main system and using SAMBA/Windows sharing or FTP to copy them across.

(Pain in the butt.  You can also use a USB stick instead of a samba share if you have your VM set to use USB devices, once the VM boots from the liveCD.  But that would be too easy)

Good luck!

--Alterax

---

