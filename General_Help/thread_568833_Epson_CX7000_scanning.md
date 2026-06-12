---
title: "Epson CX7000 scanning??"
date: 2007-10-06
forum: General Help
---

### Post by bbbaldie on 2007-10-06
Ubuntu user since the day Feisty was released :).

I have everything working nicely. I found a printer driver that works perfectly with my Epson CX7000F all-in-one. However, I have not been able to get Xsane to play ball with it.

I have added the scanner's usb product id and device id to /etc/sane.d/epson.conf. (usb 0x04b8 0x0831).

When I run sudo sane-find-scanner I get this message:

found USB scanner (vendor=0x04b8 [Language Error], product=0x0831 [Language Error]) at libusb:002:016

When i run sudo scanimage -L, I get this:

found USB scanner (vendor=0x04b8 [Language Error], product=0x0831 [Language Error]) at libusb:002:016

Followed by the enticing sound of the scanner making some noise.

Is there any hope for a solution? I have searched for help until I'm blue in the face.

Thanks.

---

### Post by linuxwizard on 2007-10-08
I don't see that scanner list here as being supported.
[http://www.sane-project.org/sane-mfgs.html#Z-EPSON](http://www.sane-project.org/sane-mfgs.html#Z-EPSON)

Also don't see that printer listed here. Trying to find some notes on it.
[http://www.openprinting.org/printer_list.cgi?make=Epson](http://www.openprinting.org/printer_list.cgi?make=Epson)

Where you got the driver for the printer I would go and look to see if their are any notes or instructions to see if they state anything about what you might have to configure  to get the scanner working.

---

### Post by va07 on 2007-10-09
Hey bbbaldie, what printer driver did you use to get the CX7000F to print properly?  I'm getting wierd printouts when I try the CX7700, and also with another one that I tried.  Any help will be greatly appreciated!

---

### Post by bbbaldie on 2007-10-10
It's a Gutenprint driver. I installed Gutenprint, and when I looked through the printer models in the CUPS config interface under drivers, it shows up there. Works dandy, too. I know it's not listed as supported on their site, but so what?:)

---

### Post by va07 on 2007-10-10
Thats funny cause I have gutenprint installed and I don't see something specifically that says 'Stylus CX7000F'.  I see 'Stylus Pro 7000', and a lot of other CX models.  I compiled and installed a new version of gutenprint but still doesn't show up.  Any chance you can check the specific printer in the Printer Manager?  Thanks.

---

### Post by bbbaldie on 2007-10-11
Strange. Here's a screenshot:

[http://ronsrecipes.com/graphics/img.png](http://ronsrecipes.com/graphics/img.png)

---

### Post by va07 on 2007-10-12
Yea I don't have that in the list for some reason.  Any chance you can post the ppd file?  It should be located in /etc/cups/ppd/

Many thanks!

---

### Post by va07 on 2007-10-12
Never mind -- I messed around and got myself a ppd file.  Here's the procedure for others who want to generate this file.

I went into the directory where I built gutenprint and did:
cd src/cups
./gutenprint.5.1 list | grep CX7000F
[ this located my printer and its many language incarnations ]
./gutenprint.5.1 cat "gutenprint.5.1://escp2-cx7000f/expert/C" > cx7000f.ppd 
[ I chose the english one and outputted to cx7000f.ppd ]

Then I chose this file when adding printers.

> **va07 said:**
> Yea I don't have that in the list for some reason.  Any chance you can post the ppd file?  It should be located in /etc/cups/ppd/

Many thanks!

---

### Post by bbbaldie on 2007-10-12
Slick. I must have done the same thing, but so long ago I forgot.

Now, if there were only some magic solution to the scanning side . . .

---

### Post by linuxwizard on 2007-10-12
Try installing Sane. Even though it is not showing it as being supported it might work. The printer wasn't listed either but it works you found the driver you needed. Of course you may go through installing Sane and may not work too.

[https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)

---

### Post by bbbaldie on 2008-01-31
Well, I have achieved harmony. I can now scan via software.

Not the best solution, but here it is:

Enable USB ports on VMWare. You do this by adding this line to /etc/fstab:

usbfs   /proc/bus/usb   usbfs   auto    0 0

Now, sudo gedit /etc/init.d/mountdevsubfs.sh

Uncomment these lines:

mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs
-obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

Then reboot. Should be able to insert a usb drive, then turn it on
through VMWare.

My (imported) XP machine would bluescreen when starting a scan. A newly-built XP machine would have communication failures.

SO, I built a Win2k machine. Works flawlessly.

Hope this helps any other frustrated CX7000 owners out there . . .

---

