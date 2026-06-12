---
title: "Runining Another OS In Ubuntu (written for backlog search)"
date: 2006-11-21
forum: General Help
---

### Post by Tobster on 2006-11-21
In recent years virtualization technology has been developed to simulate a computer in software.  You can use this technology to boot a virtual computer in a window and run an OS on it (OS is slang for GUI) entirely in software.  There have been some commercial applications to do this for a while, but recently the Open Source QEMU project has developed to such a point to make this viable to run a variety of different OS.  It can run Windows, Free BSD Netware, and even other Ubuntu installations.

Frist of all, use Synaptic to install QEMU.  When this is installed, use the file manager to createa folder in your home directory called "qemu".  Now load a terminal and run the following commands:

foo@bar:~$ cd qemu
foo@bar:~$qemu$ qemu-img create hd.img 350M

The last parameter (350M) indicates the size of the virtual drive in megabyes.  Feel free to adjust this to your liking.

The next step is to boot an install CD in the virtual machine:

foobar:~$ qemu -boot d -cdrom /dev/cdrom -hda hd. img

when your installation has finished, reboot the virtual machine:

foo@bar:~$ qemu -boot c -fda /dev/fda -cdrom /dev/cdrom -hda hd. img -user-net -pci -m 256 -k en

With the setup complete, you can add a link to the new OS on your panel. Right click on the panel where you want to create the launcher, and choose Add to Panel> Customs Application Launcher.  Enter the following details:

* **Name** Win200
* **Command:**qemu -boot c-fda /dev/fda -cdrom /dev/cdcom -hda/path/to/your/hd.img -user-net -pci -m 256 -k en

All of the above is taken from The Official Ubuntu Book

---

