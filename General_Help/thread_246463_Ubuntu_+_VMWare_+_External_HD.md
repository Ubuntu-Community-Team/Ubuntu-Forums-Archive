---
title: "Ubuntu + VMWare + External HD?"
date: 2006-08-29
forum: General Help
---

### Post by XaeroDegreaz on 2006-08-29
Hi, I'm running Ubuntu, and VMWare. I have Windows 2003 Server RS running as a guest OS. I also have a 350GB External HD that I want to use from within the guest OS.

I was wondering how this would be done, because it doesn't pop up with the "Installing" bubble when I connect the ExtHDD to the USB.

I was kinda hoping that I could do this because it's a lot easier method of file sharing between the Ubuntu and Windows guest; IE I could put the file on the ExtHDD on Ubuntu, and open the ExtHDD in the Windows guest and retrieve the file from there. I am currently running an FTP server on the Windows guest, and transfering filed from Ubuntu via that ftp server.

I just want to eliminate that if possible. It is a pain pulling off all of the bakcups that I made that are stored on the ExtHDD I put there before installing Ubuntu and shooting them throught the FTP ;). I just want to eliminate the middle man if possible.

Thanks to any help that someone can gie, I have looked through the forums and couldnt find anything.

TIA

---

### Post by XaeroDegreaz on 2006-08-30
NB

I have found the button in the VM menu that says connect usb device to guest. It pops up in my guest os, but funny thing is, it is nowhere to be found when I look for it. No external hard drive icon anywhere, besides in the taskbar where it says "Safely remove hardware".

---

### Post by GadgetsGuy on 2006-08-30
I believe that adding a USB device to VM >> Settings >> Devices >> +add will let VMWare server see your external HDD

---

