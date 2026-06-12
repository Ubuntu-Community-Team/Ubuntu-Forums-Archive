---
title: "usb server install"
date: 2013-04-01
forum: General Help
---

### Post by conradin on 2013-04-01
Hi all,
I am tryingto boot 12.04 server  edition from a USB stick which works, until some point in the installer where it trys to mount the cd-rom.
Ah, but there is no cd-rom, this is a USB drive. but is wont let me proceed with installing.
is this a bug? How do i install 12.04 ubuntu server from a usb boot device?

---

### Post by nerdtron on 2013-04-01
How did you created the bootable USB stick? Are you sure the Ubuntu ISO is not corrupt?

---

### Post by conradin on 2013-04-01
I made a VM with the same ISO today before trying to on the USB stick creator. 
I dont understand why its trying to mount the cd-rom, its not dev/cd-rom its where ever teh boot media is.
i guess i can try reburning the device.

---

### Post by steeldriver on 2013-04-01
I had a similar problem with the alternate ISO a while back I think - some info and possible workarounds here

[http://askubuntu.com/questions/127398/usb-drive-install-of-ubuntu-12-04-server-fails-cant-find-components-from-cd-r](http://askubuntu.com/questions/127398/usb-drive-install-of-ubuntu-12-04-server-fails-cant-find-components-from-cd-r)

---

### Post by nerdtron on 2013-04-01
> **conradin said:**
> I made a VM with the same ISO today before trying to on the USB stick creator. 
I dont understand why its trying to mount the cd-rom, its not dev/cd-rom its where ever teh boot media is.
i guess i can try reburning the device.

I always burn Ubuntu ISO using Unetbootin [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
Always works, every single time :)

---

### Post by conradin on 2013-04-01
*sigh*
I believe This is a kernel bug, some sort of regression, or a change made to the installer. The media checks fine. 
but I need a server up and running like 2 hours ago, so I tired Lucid Lynx server, and its working perfect. 
I get frustrated, Theres so many features in the newer versions I want to use, but every time i try to migrate over, something stupid happens, or doesn't work right. 
i give up. thread closed.

for giggles, i should burn a disk from 120.4 server, then boot from a usb. Then when it asks for a mount point to the CD-Rom, I should stick a CD-Rom in there, and see if it resolves the mounting issue. Surely I'm not the only one witnessing this, or trying to install 12.04 server from a usb harddrive.

---

