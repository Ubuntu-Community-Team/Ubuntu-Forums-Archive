---
title: "Can't remove failed printer"
date: 2020-10-21
forum: General Help
---

### Post by knight69 on 2020-10-21
I have a Brother HL-3170CDW printer on my network that used to work fine on Ubuntu 18.04 until I upgraded to Ubuntu 20.04 with Gnome.

The Brother printer driver installation tool (supposedly) installed the driver for the network printer, but when I open the printer settings utility it shows 2 printers, HL-3170CDW and
Brother_HL_3170CDW_Series, neither of which will print a pdf file, or a graphic file. I can get one of them to print a simple text file so long as it has no graphics.

One of the error messages I get is:  ```
[21/Oct/2020:22:29:21 -0400] [Job 9] The printer is unreachable at this time.
``` but I can ping the printer and access it with the browswer.
Another error message is:  ```
[21/Oct/2020:22:33:53 -0400] [Job 11] No suitable destination host found by cups-browsed.
```
Another error message is:  ```
[21/Oct/2020:23:01:40 -0400] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id \'Brother_HL_3170CDW_series-DeviceN..\' already exists
```

The configuration settings tool isn't any help as I have no idea where to find the drivers and I can't seem to make any changes to the settings that stick. 

I have tried to uninstall both printers, but when I uninstall them, they disappear momentarily and then pop right back up.  I installed the system-config-printer app and tried to delete them with that, but the same thing happened. 

I am at a total loss to know how to uninstall this printer and would appreciate any help.

---

### Post by col48 on 2020-10-23
I see you have not had any replies yet.  I have no idea if this will help, but it might provoke someone who knows what happens in the engine room to suggest something better....


I had changed printers - same model but different piece of equipment.  I had not uninstalled anything as the same driver was still the right one.  But after the change I was sometimes being invited to choose between a ghost printer (just called 'printer') and the real one, identified by brand and model.  The ghost was the default, and anything sent there neither printed nor raised an error.

This was what was suggested, probably on this forum:

To stop programs from showing auto-discovered printers in the print dialog, you need to reconfigure the avahi daemon service:

sudo gedit /etc/avahi/avahi-daemon.conf
   in the [server] section, add
enable-dbus=no

do system restart (merely “sudo service avahi-daemon restart” did not work for me)

Once I configured avahi like this, I no longer saw this ghost printer.

---

### Post by knight69 on 2020-10-23
Enable-dbus was set to yes, but it was commented out, so I have no idea what the default was. I uncommented it and changed it to no and that got rid of the ghost printers, but I still had problems with installing the printer. I finally managed to get it installed and working. 

First, I had to locate all the files with the printer model number, most of which were in the /opt directory under Brother. I simply deleted the entire directory. I deleted an executable from the /usr/bin directory that had the model number on it and a couple of others. I also used the browser (localhost:631/printers and deleted all printers. I used dpkg -l | grep printer-model to find any printer packages and deleted everything I could find related to the printer.

Then I reviewed the installation script only to find out it was attempting to install the wrong printer, so I trashed that and did a forced instalation of the driver repositories I downloaded from Brother using dpkg --force all . That set up the printer, but as a local usb printer, not a network printer. I was able to change the location using system-config-printer. (The printer settings tool in the gnome control center now seems to be broken, but was never that useful in the past when it was working.)

I have the strong feeling that what I did is not the recommended procedure, but having followed suggestions from about 20 people with no success, I resorted to drastic measures.  Hopefully, I didn't screw up my computer too badly. At least the printer is working.

---

