---
title: "Anyone running Windows as guest in  a VM?"
date: 2007-11-01
forum: General Help
---

### Post by singlewc on 2007-11-01
I cannot leave the dark side to be a full time Ubunt'er because of GPS, PocketPC, scanner, and a few other items, all of which are dependent on USB as the interface.

I am wanting to  know if there is a VM, such as virtual  box, or some other virtual software that Ubuntu can run as a host, which will allow syncing with a PDA, or GPS, and allow more choices for scanners, etc?

Anyone doing this successfully? If so, I would sure like to hear from you.

Thanks,

John

---

### Post by windom on 2007-11-05
I installed XP in VMWare Server. It was a pretty straightforward process. I use it for GPS. Alas, I cannot find a GPS program for linux that even comes close to what is available for windows, but that's another topic. As I recall you have to make sure you have the required devices in the VM. I had to add USB since my gps receiver is USB. After it is plugged in, one needs to remove the gps module cdc_acm. VMWare can not use a USB device if linux is using it. The first time using the gps receiver you will, of course, have to install the window's driver but after that you'll just have to unload the linux driver before using the GPS program. It's been a while but this is what I recall.

-w-

---

### Post by singlewc on 2007-11-05
> **windom said:**
> I installed XP in VMWare Server. It was a pretty straightforward process. I use it for GPS. Alas, I cannot find a GPS program for linux that even comes close to what is available for windows, but that's another topic. As I recall you have to make sure you have the required devices in the VM. I had to add USB since my gps receiver is USB. After it is plugged in, one needs to remove the gps module cdc_acm. VMWare can not use a USB device if linux is using it. The first time using the gps receiver you will, of course, have to install the window's driver but after that you'll just have to unload the linux driver before using the GPS program. It's been a while but this is what I recall.

-w-

Thanks. If I can get my install video working, posted elsewhere, I will see about getting Vmware up and running. I appreciate the tip about removing the device from linux first. Probably would have missed that.

John

---

### Post by fjgaude on 2007-11-05
I run VMware Server, it's free, and it works just fine with Windows XP Pro SP2, for all the Windows programs I've installed. Speed is good, copy and paster between Linux and Windows, everything just works. It's just like you are in Windows because you are, printers, scanners, USBs, etc.

---

### Post by singlewc on 2007-11-05
> **fjgaude said:**
> I run VMware Server, it's free, and it works just fine with Windows XP Pro SP2, for all the Windows programs I've installed. Speed is good, copy and paster between Linux and Windows, everything just works. It's just like you are in Windows because you are, printers, scanners, USBs, etc.

I am hardly a guru, so will I be excited at the requirements to install :-)

Any comments or advice will be happily received.

Thanks,

John

---

### Post by fjgaude on 2007-11-05
Here's what my desktop looks like when in the vm window: It's big for graphic design work but doesn't show here, 1600x1200 dpi.

---

### Post by buntunub on 2007-11-05
Hi. I use VirtualboxOSE and have XP running in it nicely. Install the Extras plugin from the tools menu (I think), and you get it all. However, I dont think any of that is necessary for what you want to do. For scanning, use Xsane, which works with my USB Printer/Scanner perfectly. For the GPS Stuff, try using wine or Crossover. There are open source apps that cover just about everything under the sun, so do some googling around and you might stumble across something really nice there. The PocketPC should sync up with Ubuntu natively, or at least it does for me without having to do anything other than plug it into the USB slot. Perhaps your having hardware issues or a bad install?.. Funny that literally everything you mention works out of the box for me on Ubuntu with open source apps.

---

### Post by ptn107 on 2007-11-05
I'm running XP Pro SP2 in Virtualbox (non-OSE, so I can use usb devices).  My advice is to use VMware server, as the usb support in virtualbox has been quirky at times in my experience.

---

### Post by fjgaude on 2007-11-05
> **ptn107 said:**
> I'm running XP Pro SP2 in Virtualbox (non-OSE, so I can use usb devices).  My advice is to use VMware server, as the usb support in virtualbox has been quirky at times in my experience.

Not only that but the cut, copy and paste to and from the clipboard between Windows and Linux is unstable. It is not in VMware Server.

---

### Post by singlewc on 2007-11-07
Amazingly, I have VMWare server installed and running fine with Windows2K :-)

Not sure I could do it again, but I guess repetition and time make us all experts.

Maybe someone can help me with the USB in the VM? Its there, its not there, its confusing. I realize that I cannot use it in both linux and vmware at the same time, but I have not been able to use it at all in the vmware desktop. 

USB is good in Ubuntu, so how do I tell Ubuntu to give it up, so the VM can have access? The comment was made about disabling it, which I realize I have to do, but I do not know how to actually disable it.

Can it be done dynamically, or is it something that requires a restart every time I change it. I can live with a few commands going in and out of vmware. Just hoping its not a massive amount of hoops to get it to give up usb, and then take it back.

Any explanations in english, as in newbie, would be appreciated very much :-)

John

---

### Post by fjgaude on 2007-11-07
Well, 7.10 has four lines commented out that need to be uncommented for USBs to work. It's not difficult to set it all right:

```
gksudo gedit /edt/init.d/mountdevsubfs.sh
```

Go down to line 42 and uncomment 42 through 45, line starting wiith mkdir to mount. (Gedit has a line counter built-in. Edit/Preferences, check Line Numbers) Save, reboot and you are done.

If you don't wish to reboot, this will likely work instead:

```
sudo /init.d/mountdevsubfs.sh restart
```

Have fun and let us know how you make out.

---

### Post by rgd55 on 2007-12-08
I tried your script,gksudo gedit /edt/init.d/mountdevsubfs.sh
and the page loaded blanc,no text whatsoever.Can you help
me?
Thanks

---

### Post by rgd55 on 2007-12-08
problem solved

---

