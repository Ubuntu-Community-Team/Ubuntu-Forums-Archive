---
title: "VMWARE Question?!?"
date: 2007-09-11
forum: General Help
---

### Post by Scott Olson on 2007-09-11
Hello,

I am in the processes of setting up vmware on my laptop and when I create a new image and try to run it, it get the following message:

PXE-E53: No boot filename received
PXE-M0F: Exiting Intel PXE ROM
Operating System not found

A windows message-box appears with just an OK button and manifests the following message:

"No bootable CD, floppy or hard disk was detected.  To install an operating system, insert a bootable CD or floppy and restart the virtual machine by clicking the reset button".

Can someone please give a noob some help!
1. Do I need a bootable CD or floppy to get this running?
2. I don't want to install an operating system, I want to use the current one from the image I created, so why is it asking me to install an OS?
3. What settings do I need to change in order to get the virtual image to work?
4. Do I always need a bootable CD?
5. Do I need to install an OS to the virtual image (makes no sense)?

I am running XP Professional on my laptop and attempting to run this image on my laptop to try it out.  I have an HP with an Intel Centrino Duo running on 2 gigs of RAM and 80 Gigs of HD.

I appreciate any assistance I can get.

Cheers,
Scott:popcorn:

---

### Post by K.Mandla on 2007-09-12
Moved to General Help. ;)

---

### Post by iAndrew on 2007-09-12
I don't know if this is right. But I'm pretty sure you need an iso, or an os boot disk.

If you have an iso, and you are using vmware workstation you can set it to mount on the virtual computer.

---

### Post by Scott Olson on 2007-09-12
Just an update:

My original understanding was that VMWARE works similar to Microsofts Virtual PC; where upon image creation, MSVPC actually makes an image.  Subsequently, the image boots up and functions just the same as the source.

However, from what I have just learned (after asking a few people) VMMWARE just builds an infrastructure.  The user must install the operating system and other software after the infrastructure is created.

So I think I have the answers to all my questions because it all now makes perfect sense as to why I need a boot disk.:lolflag:

Cheers,
Scott:popcorn:

---

