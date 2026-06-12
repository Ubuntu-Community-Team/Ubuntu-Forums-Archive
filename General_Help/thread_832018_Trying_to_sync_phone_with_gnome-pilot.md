---
title: "Trying to sync phone with gnome-pilot"
date: 2008-06-17
forum: General Help
---

### Post by moyam01 on 2008-06-17
Hi. First Post

I switched to ubuntu a couple of weeks ago, and I am very happy. I am still in the conversion process, but all of my hardware issues are pretty much resolved (thank you for the nvidia driver update), I have most of the productivity stuff installed (I used wine to install office 07, but I found openoffice to be just as good), as well as a couple of cool apps (supertux 2 is awesome), and am trying to learn as much as I can about the command line, and maybe a little python.


Well, yesterday I began using evolution for it's task list, calendar and contacts options. I was able to export my calendar and contacts in vCalendar and vCard formats from outlook 07, and imported them successfully into Evolution.

Then, I tried to use gnome-pilot to sync my Treo 650 to the calendar, and when I went through the wizard and got to the part about finding the phone ID (i had previously synced with windows) nothing happened. I tried all of the options under the connection methods, and nothing happened except for when I selected USB0, which I got the following error:

"Failed to connect using device 'cradle' on port '/dev/ttyUSB1'. Check your configuration, as you requested old style usbserial 'ttyUSB' syncing, but do not have the usbserial 'visor' kernel module loaded. You may need to select 'usb:' device."

I tried selecting 'usb:' as a connection method, but again, nothing happened. I then googled the problem and got this articles:

[http://www.h8n.com/tiki-index.php?page=Treo+650+setup+with+Ubuntu](http://www.h8n.com/tiki-index.php?page=Treo+650+setup+with+Ubuntu)
[https://help.ubuntu.com/community/PalmDeviceSetup](https://help.ubuntu.com/community/PalmDeviceSetup)

I tried them both and they both failed. If someone could point me in the right direction that would be great ( a step by step would be much appreciated.

My setup:

Core 2 Duo E6600
nVidia 8600 GT
EVGA 680i mohterboard
2x 360 GB HD (one personal data nad one ubuntu/windows dual boot)

Thanks for your time.

---

### Post by moyam01 on 2008-06-17
Anybody?

---

### Post by moyam01 on 2008-06-18
Was able to to find this article and got it to work:

[http://taquoriaan.com/2008/02/27/how-to-syncing-pda-using-usb-in-ubuntu-linux/](http://taquoriaan.com/2008/02/27/how-to-syncing-pda-using-usb-in-ubuntu-linux/)

For anyones refrence

---

