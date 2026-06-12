---
title: "installing Dell  printer in Gutsy"
date: 2008-03-11
forum: General Help
---

### Post by kurreburre on 2008-03-11
Hi everyone

I have a really cumbersome problem with printing in XUbuntu. I can't get it to work. I have an old compaq computer witn a PIII 800 Mhz and 128MB of mem and a Dell A920 printer. When I turn on the printer management tool installed with XUbuntu, it finds the printer, and when I try to print to it, the document arrives in the printer queue and is later removed, so it looks like everything goes just fine. The problem is that the printer does not do anything at all, not a sound. If the drivers were incorrect wouldn't that result in crap figures and not being able to print pictures etc?? I have tried to read the cups manual, set it up as a samba printer etc, but nothing works. Then I read a post here in the forum, from someone with a similar problem, that had used something called" Foomatic GUI printer", and then got evrything to work. I tried to install that one, but it seems like it is not supported by XUbuntu (might be only Gnome).
I am not that familiar with printing in Linux so can someone help me out here??

Best regards



Pär

---

### Post by linuxwizard on 2008-03-11
Dell printers are made by Lexmark. According to this > [http://www.openprinting.org/show_printer.cgi?recnum=Dell-AIO_Printer_A920](http://www.openprinting.org/show_printer.cgi?recnum=Dell-AIO_Printer_A920) > your printer is the same as  Lexmark X1270 and needs the driver Z600.

---

### Post by kurreburre on 2008-03-12
OK thank you.

I also found a realy nice FAQ section in the same page. But maybe you or someone can answer another question that I have not found any answer on.
If I want to use my Linux computer as a printer server using samba, do I need to install this printer driver ?? When I define a printer in samba, saying that it should use the local driver (the driver on the windows client) nothing happens. I assume that samba does not know that I have a printer on my usb port. How do I tell samba to send the print job to usb1??
Sorry for all the questions... I am a newbie on Linux, and I have found most of the things pretty simpe, setting up apache, installing samba, installing joomla etc, but printing is a monster. You have Cups you have  lpr, you have foomatic, samba, spoolers and so on... what the heck is the plan?? Sorry for the frustration, but  after 1 month I still havn't got my printer to work *ynf*

Cheers


Pär

---

### Post by kurreburre on 2008-03-12
By the way I tried foomatic, but the z600 driver was not in the database that came with my dist (gutsy), so this was was also not to any use...

Cheers again.


Pär

---

### Post by kurreburre on 2008-03-12
hi again

I found this nice howto in the linuxprinting org site. Saying that I should have this directory

/proc/bus/usb/drivers

Which I do not have. So further the guide said that I should mount a file system like this

mount -t usbdevfs none /proc/bus/usb.

... which gives me this error: mount: unknown filesystem type 'usbdevfs'

when I look in my kern.log the usb entries looks like this:

kern.log.0:Mar  1 08:54:29 pke-server kernel: [   23.232295] USB Universal Host Controller Interface driver v3.0
kern.log.0:Mar  1 08:54:29 pke-server kernel: [   23.971433] uhci_hcd 0000:00:14.2: new USB bus registered, assigned bus number 1
kern.log.0:Mar  1 08:54:29 pke-server kernel: [   23.971956] hub 1-0:1.0: USB hub found
kern.log.0:Mar  1 08:54:29 pke-server kernel: [   24.313601] usb 1-1: new low speed USB device using uhci_hcd and address 2
kern.log.0:Mar  1 08:54:29 pke-server kernel: [   24.749571] usb 1-2: new full speed USB device using uhci_hcd and address 3
kern.log.0:Mar  1 08:54:29 pke-server kernel: [   24.928596] hub 1-2:1.0: USB hub found
kern.log.0:Mar  1 08:54:29 pke-server kernel: [   25.239343] usb 1-2.1: new full speed USB device using uhci_hcd and address 4
kern.log.0:Mar  1 08:54:29 pke-server kernel: [   25.591271] usb 1-2.2: new full speed USB device using uhci_hcd and address 5
kern.log.0:Mar  1 08:54:29 pke-server kernel: [   25.749374] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:14.2-1
kern.log.0:Mar  1 08:54:29 pke-server kernel: [   25.749441] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
kern.log.0:Mar  1 08:54:29 pke-server kernel: [   49.836072] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 5 if 0 alt 0 proto 2 vid 0x413C pid 0x5106
kern.log.0:Mar  1 08:54:29 pke-server kernel: [   49.836148] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
kern.log.0:Mar  1 11:07:16 pke-server kernel: [ 8021.356781] usb 1-2: USB disconnect, address 3
kern.log.0:Mar  1 11:07:16 pke-server kernel: [ 8021.356797] usb 1-2.1: USB disconnect, address 4
kern.log.0:Mar  1 11:07:16 pke-server kernel: [ 8021.357369] usb 1-2.2: USB disconnect, address 5

So does anyone have any idea??

Cheers

---

### Post by linuxwizard on 2008-03-12
From here > [http://ubuntuforums.org/showthread.php?t=555522](http://ubuntuforums.org/showthread.php?t=555522) > MUST INSTALL BOTH OF THESE


[http://leighm.dgtlmoon.com/misc/bina...1.0-2_i386.deb](http://leighm.dgtlmoon.com/misc/bina...1.0-2_i386.deb)

[http://leighm.dgtlmoon.com/misc/bina...2.0-2_i386.deb](http://leighm.dgtlmoon.com/misc/bina...2.0-2_i386.deb)

USE THE GDEBIAN PACKAGE INSTALLER

GO TO PRINTERS AND U SHOULD FIND THE Z600 UNDER DRIVERS USE THIS FOR THE X1270

---

### Post by kurreburre on 2008-03-13
Thanks again

This helped out alot (I think), however in the instructions I have found on the internet one should test the backend system by typing.

    /usr/lib/cups/backend/z600

and the output should be somthing like this:

    direct z600:/dev/usb/lp0 "Lexmark  Lexmark 510 Series" "Lexmark Printer"

However I get nothing and furhter on it says that I should add this line to fstab 

    usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0

and then mount it. however I still do not get any reply from the ./z600 command

Anyone have any idea??

---

### Post by linuxwizard on 2008-03-13
I am not sure what you are trying to do. Did you install these 2 deb packages from my last post ? Than go and add and setup your printer to see if it would work ? I don't use Lexmark printers. I have 3 HP printers I plug them in than add the printers and have all of them setup in less than 10 minutes.

---

