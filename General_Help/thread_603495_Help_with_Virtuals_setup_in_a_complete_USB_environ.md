---
title: "Help with Virtuals setup in a complete USB environment"
date: 2007-11-05
forum: General Help
---

### Post by Solarus on 2007-11-05
Hey Guys

I am currently attempting to put together a complete operating system and virtual environment using only a large pen drive.  I have the installation and the configuration of the Host system pretty well sorted…..  I think.  Everything is very stable and I have currently tested the USB device across 3 different platforms with the system successfully booting and configuring the hardware for each without too many issues.

My problems are occurring when I try and configure any virtual machine’s to run on the system.  I have currently tried running Virtual Box and VMware Workstation.  Both systems install and configure without any errors.  I have setup the virtual disks (all on the USB stick) however, when I try to run the installation of XP with Integrated sp2 it boots the cd, goes to the installation screen and errors when it gets to the acpi.sys file.  It says that the file is corrupted however, I know there is nothing wrong with the disk however, to confirm this I have mounted the .iso as an image to confirm and received the same error.  

I am guessing that this error is due to me wanting to do all of this with a large usb pen however, I can’t find any reason why this is happening.

Does anyone have any suggestions ?

Configuration:  Various Hardware however ubuntu 7.10

---

### Post by Solarus on 2007-11-05
bump

---

### Post by Solarus on 2007-11-05
Anyone?

---

### Post by g2g591 on 2007-11-05
I'd say that no one knows the answer (its not everyday someone installs windows in a virtual environment, especially from a usb stick)

---

### Post by Nesmontu on 2007-11-05
Which virtual machine are you using? I know that with KVM+qemu, you have to install Windows without ACPI support (at least if you want it to run at a usable speed). You can select this at install time, see [here]("http://kvm.qumranet.com/kvmwiki/Windows_ACPI_Workaround") for a howto. Might work with other VM's too?

---

### Post by Solarus on 2007-11-06
Thanks, I'll give it a shot

I am trying Vitual Box and vmware.
Thanks

---

### Post by Solarus on 2007-11-06
Well unfortunately that didn't work and I am still getting the same errors.

Te error is showing up during performing the XP Pro Installation.  Message is:

"The File ACPI.sys is corrupted" Press any key to continue. 

It then proceeds to reboot and try again :-(

Anyone else?

---

### Post by Solarus on 2007-11-10
hey guys.  Does anyoone have any assistance for me?

---

