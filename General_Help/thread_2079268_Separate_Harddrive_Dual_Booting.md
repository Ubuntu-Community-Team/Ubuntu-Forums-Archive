---
title: "Separate Harddrive Dual Booting"
date: 2012-11-01
forum: General Help
---

### Post by Jcpayne on 2012-11-01
Windows 8 is installed on one harddrive, Ubuntu 12.0.4 is installed on a separate harddrive.  How can I work this so that I'm prompted for an operating system choice upon computer startup?
 
Thanks
 
jc

---

### Post by oldfred on 2012-11-01
Have you run?

sudo update-grub

But some have had issues. If that does not work create a login to launchpad and add to this bug.

Drivemap bug - two drives each boot from BIOS, but grub does not chainload
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1073630](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1073630)

---

### Post by Jcpayne on 2012-11-03
Sorry, I don't really understand the instructions.

My main boot harddrive boots windows, do i need to log in to ubuntu and add something so that it adds a boot menu to my windows boot manager?
Or what exactly is the process?
I'm new, and need details.

---

### Post by oldfred on 2012-11-03
Did grub install to the other drive, so if you change boot drives in BIOS or with one time boot key (f12 on my system, but varies) does Ubuntu boot?

If not boot liveCD or USB that you used to install, run as liveCD and download this:

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Slug71 on 2012-11-04
Im assuming you installed Ubuntu second. If you don't get a menu at boot already, then Ubuntu most likely installed the bootloader to the drive that is NOT set to boot first. Go into BIOS and change the boot order of your drives.

If you installed Windows 8 after Ubuntu, then it's likely overwritten the bootloader. You'll need to mount your Ubuntu install from a Live CD and update-grub or reinstall it. Alternatively you can also use a Grub repair disk.

---

