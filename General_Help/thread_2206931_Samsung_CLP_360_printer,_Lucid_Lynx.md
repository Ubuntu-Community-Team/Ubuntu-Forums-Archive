---
title: "Samsung CLP 360 printer, Lucid Lynx"
date: 2014-02-21
forum: General Help
---

### Post by HC48 on 2014-02-21
I have Ubuntu Lucid Lynx.
I managed to install my new samsung CLP 360 printer, did a few tests and everything worked. It appeared in my system menu printer manager so all was well.
When trying to print an Adobe p.d.f document the printer didn't print the A4 document correctly, it didn't fit the page, I tried to adjust the settings and use GIMP to no avail. I decided to abandon and try again later.
The next time I switched on the printer the configuration panel had disappeared from the system menu, when clicking on the printer icon it tries to start the printer but I don't get the printer manager. I also get an error page from the printer telling me to check the connection, which I have done, moving the usb cable to a different port which I know does work.
I have reinstalled the printer, but I couldn't remove it beforehand, not having the printer manager. I don't know how to do it in the terminal although I suppose I could try with the right command...maybe someone could give it to me.
I have tried reinstalling python 2.6 and adding more libxml packages, and various commands as advised in other forums (eg. sudo system-config-printer, sudo apt-get install system-config-printer_gnome) , but no-one seems to have had exactly the same problem in my version of Ubuntu (10.04) and nothing I have tried has made any difference.
The icon is ticked in the main menu in preferences.:p
I should be grateful for any help. I might be missing something which is obvious to more experienced members...

---

### Post by mörgæs on 2014-02-21
New hardware and old software is a bad combination. 
I suggest that you take a backup of your user files and do a fresh install of 13.10 as a first step. Please write again if the printer still does not work well after that.

---

### Post by HC48 on 2014-02-22
Thank you mörgaes, i'm not surprised. I think I'll try that as my computer is getting on a bit. I may need new hardware anyway.
Have a good day.

---

### Post by mörgæs on 2014-02-22
If the hardware is getting slow then Lubuntu is worth trying.

---

### Post by HC48 on 2014-02-22
OK, thanks for the tip. :)

---

### Post by mörgæs on 2014-02-22
You are welcome.
Please post back and tell if it worked.

---

### Post by HC48 on 2014-02-22
Before I change everything I'm still trying to get back to normal. My printer was working at first after all.
I tried this which worked for someone with a similar problem:

sudo apt-get --reinstall install system-config-printer-gnome

([https://answers.launchpad.net/ubuntu/+source/ubuntu-docs/+question/109987](https://answers.launchpad.net/ubuntu/+source/ubuntu-docs/+question/109987))


but it didn't work for me, I still  have no printer management in the system admin menu, when I click on the printer icon which is still there, it tries to launch the printer.

I also did:

sudo lpstat -s

my printer is there as default.
I shall be trying a different usb cable when I can find one.

---

