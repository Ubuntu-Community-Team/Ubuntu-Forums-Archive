---
title: "installing grub"
date: 2015-08-20
forum: General Help
---

### Post by Adrian_Moncloa on 2015-08-20
I cannot install grub on an ASUS laptop that has the ubuntu command line only.
My first question is does the machine need to be connected to the internet for sudo apt-get install grub to be successful?

My second question is once I get the grub prompt, how can I use it so the machine boots from a usb stick that has ubuntu on it which I want to reinstall.

Thanks

---

### Post by yancek on 2015-08-20
> My first question is does the machine need to be connected to the internet for sudo apt-get install grub to be successful?

Yes, generally speaking that is the case as normally you are downloading from the Ubuntu repositories/servers.

> My second question is once I get the grub prompt, how can I use it so  the machine boots from a usb stick that has ubuntu on it which I want to  reinstal

Grub prompt from what?  an installed system?  from the flash drive?  To boot the usb stick to install Ubuntu, you need to set it to first boot priority in the BIOS immediately on boot.  The key to use varies with manufacturer but it should show at the bottom of the screen when you initially boot. 

If you don't have Grub installed, how would you get to a command line?  You might give more details on exactly what you are trying to do and how because booting from a usb stick to install isn't that difficult if the stick was created correctly which brings us to 'how did you create the usb stick'?

---

### Post by Adrian_Moncloa on 2015-08-20
Thank-you for answering the first part of my question

Somebody botched up an install of Ubuntu on an Asus Computer running XP.  All that is available on that computer is the ubuntu command line.  I think the best solution to get a Ubuntu GUI is to reinstall Ubuntu from a USB stick. I have a USB drive with 32 bit Ubuntu on it that I think is bootable.  I used the software ACtive@Boot Disk to make the USB stick from an iso file.  I have another XP machine but was unable to test the USB stick there because USB was not listed in its BIOS. 

The BIOS on the ASUS only lists one option : HDD  as a bootable option; that is the Windows XP bios I believe.  What I am trying to do is get GRUB to list the USB drive as its first bootable option since I think the computer is using GRUB whenever it reboots. Weather I can do that from a grub prompt or by manually reconfiguring some files I do not know.

A separate problem I have is connecting this computer to my wifi from the command line.  I have seen posts that require the use of network manager but it seems I need an internet connection to install network manager as well. I tried calling my ISP but they could not help me. Thanks in advance for your help.

---

### Post by yancek on 2015-08-20
> The BIOS on the ASUS only lists one option : HDD  as a bootable option

On many computers, that is where usb drives are shown.  If you have a flash drive, it should be shown here usually by name.  If you have a Sandisk flash drive, Sandisk should show.  If it is Toshiba, Toshiba should show.  If it doesn't show in the BIOS, you may not be able to boot from usb on the machine. 

> ACtive@Boot Disk 

I'm not familiar with this software.  Since you can't test on another machine, we don't even know if the disk is bootable.  It is possible to directly boot the Ubuntu iso file and install it to your computer.  Which version of Ubuntu are you using?  Do you have the iso file on the Ubuntu partition?  If not where is it?  If it is on the Ubuntu partition, someone should be able to tell you how to edit the grub.cfg file to boot to install.

---

### Post by Bucky Ball on 2015-08-21
```
sudo grub-install /dev/sda
```

... presuming you want grub on the first hard drive. 

If this is a broken Ubuntu install only, what makes you think grub is not already there? Unless someone has manually uninstalled it, highly unlikely, you just need to run the above command and let us know of any error messages or outcomes.

You don't tweak grub to boot from USB. You set the BIOS to boot from USB or use the appropriate key to bring up a list of boot devices at startup. You can do that now without going through any of the rest of it if you just want to reinstall Ubuntu.

Bottom line: if you just want to reinstall Ubuntu then tweaking with the grub has got nothing to do with it. Plug in your USB and boot from it by setting the BIOS or choosing from the device list at boot (try hitting F12 or F9, the appropriate key will be shown on the screen right at startup, but it will be quick ... try checking the manual).

---

### Post by Adrian_Moncloa on 2015-08-21
Thanks for your comments,  I was able to load Ubuntu by changing the BIOS.

---

### Post by Bucky Ball on 2015-08-21
Good news. Please mark the thread as solved. See the first link in my signature. Good luck. :)

---

