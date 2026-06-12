---
title: "VMWare Player problem with installing OS"
date: 2007-05-02
forum: General Help
---

### Post by pmdkh on 2007-05-02
I am having some trouble with VMWare Player.  I have installed it, but I can't get it to load an OS.  I am using Dapper Drake, and I want the guest OS to be WinXP Pro.  I installed it by downloading the .tar.gz from VMWare's web site and running the installation script.  I had tried downloading the vmware-player package, but the kernel version wasn't matching up, and I couldn't figure out how to fix it.

This is what I am doing:

I put my Windows XP disk in the CD-ROM.  I go to Applications --> System Tools --> VMWare Player.  I click on the .vmx file that I downloaded from the Ubuntu Help pages.  [https://help.ubuntu.com/community/VMware/Player]("https://help.ubuntu.com/community/VMware/Player")

After this, VMWare Player seems to be starting up.  I then get a message that says that "No bootable CD, floppy, or hard disk was detected.  To install an operating system, insert a bootable CD or floppy and restart the virtual machine by clicking the Reset button."

In [this thread]("http://ubuntuforums.org/showthread.php?t=342631"), it talks about making sure the .vmx is configured to see your CD-ROM, and I have already done this.

Does anyone know what is wrong?

---

### Post by raja on 2007-05-02
[Easyvmx]("www.easyvmx.com/") provides a very friendly way of making a virtual machine. I would recommend you try that. The other thing you could do is check if your system itself can recognize the disk and boot from it (to be sure it works). You can also show us your vmx file here - may help.

---

### Post by pmdkh on 2007-05-02
I just tried to boot from my WinXP CD, but it didn't work.  So obviously that's the problem.  I'll have to find out why the WinXP CD won't boot, then return to VMWare Player later.

---

### Post by raja on 2007-05-02
There are atleast some XP install cds that are not bootable. They are intended for updating a pre-existing windows install. Have a look at Bart's PE builder which you can use to create a bootable windows cd.

---

### Post by Unconscious on 2007-05-02
I had the same problem. I had to make an ISO from the installation CD.

Right-click on the CD-ROM icon on your desktop, select Copy, and specify the file location to be the same directory as your .vmx

Edit your .vmx, with your favorite text editor, modifying these entries:

> ide1:0.present = "TRUE"
ide1:0.fileName = "Win2kPro.iso"  # or whatever your file name is
ide1:0.deviceType = "cdrom-image"


It worked for me.

---

