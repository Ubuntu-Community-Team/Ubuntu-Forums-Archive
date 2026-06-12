---
title: "HP Photosmart C4480"
date: 2014-11-24
forum: General Help
---

### Post by whizkidmann on 2014-11-24
Hello first time poster here, I am trying to install the HP Photosmart C4480 on Ubuntu 14.04 64bit.
I tried using the built-in Ubuntu Printers app, but it will not print anything or scan. Also it detects the printer connected through Paralell port.
I then attempted to install it using the HPLIP 3.14.10 app, but it will not detect the printer when connected and detecting through USB. 
The Paralell port(LPT) connection mode through the HPLIP app is greyed out for some reason.

Any help on the situation will be greatly appreciated.

---

### Post by pqwoerituytrueiwoq on 2014-11-24
does it support USB? that should make it literally plug and play, i have not used a parallel port on over 10 years, i dont even have any to use

---

### Post by whizkidmann on 2014-11-24
Ah, probably should have clarified, when connecting through USB (Only connection mode available) it will detect it as if it was parallel to the built-in app.

---

### Post by pqwoerituytrueiwoq on 2014-11-24
in my exp with hp printers you just connect the usb cable to the ubuntu box while it is on and logged in and it auto configures it self and just works, unless you need a newer driver, but that printer is from what 2008
if you run [FONT=courier new]scanimage -L[/FONT] does it list your scanner? if so any scanning software can scan

---

### Post by rbmorse on 2014-11-24
The HPLIP web site [http://hplipopensource.com/hplip-web/models/photosmart/photosmart_c4400_series.html](http://hplipopensource.com/hplip-web/models/photosmart/photosmart_c4400_series.html) indicates your printer is supported via the USB connection.  

I'm not sure what you mean by "[COLOR=#000000]it will detect it as if it was parallel to the built-in app." Is this something on the printer itself?  


[/COLOR]

---

### Post by whizkidmann on 2014-11-25
[ 						 							]("http://ubuntuforums.org/member.php?u=865458")[**[COLOR=#000000]pqwoerituytrueiwoq[/COLOR]**]("http://ubuntuforums.org/member.php?u=865458") the command doesn't pick up the scanner.
				 				 					 						 	[**[COLOR=#000000]rbmorse[/COLOR]**]("http://ubuntuforums.org/member.php?u=82") when I attempt to add the printer through the Printers app, it will tell me it is a local printer connected by parallel. Despite being connected through USB

---

### Post by pqwoerituytrueiwoq on 2014-11-25
does it show up in lsusb?
```
lsusb | egrep -i 'HP|Hewlett|Packard|PhotoSmart'
```
if not i would guess your usb cable is bad or the printer is off

can you run scanimage -L from a stock config live cd? (i have never had to use any special HP app on linux, at most i use a hplip ppa and upgrade)

---

### Post by whizkidmann on 2014-11-25
I have replaced the cable with a known working one, and that didn't solve the problem.
I also tried using the scanner and printer on a live cd boot, but still with no results :/

---

### Post by rbmorse on 2014-11-25
open a terminal and type:

hp-toolbox<return>  where <return> means press the return or enter key on the keyboard. 

when the toolbox opens, remove any instances of the printer that may exist. Close the toolbox.  Open the Ubuntu printer utility, and remove any instances of the printer that may exist.  close the printer utility. Reboot the machine, or alternatively, stop and restart CUPS. 

make sure the printer is powered on, connected, and otherwise ready to print (ink and paper loaded)

Open a terminal, type:

 hp-toolbox<return>

when the toolbox opens select "device" then "setup device" and try to install the printer from the toolbox. 

If the printer does not install properly, or does not work after installing via the hp-toolbox, use the "diagnose queues" and "diagnose HPLIP driver" wizards and attempt to localize the problem.

---

### Post by whizkidmann on 2014-11-27
I attempted you fix, but it did not work.
As for the diagnose tools, I can't see where these are? In the terminal or the GUI?

---

### Post by rbmorse on 2014-11-27
They're in the hp-toolbox application that should have been installed when you installed hplip and hplip-gui from repository

---

### Post by JeQhdMD on 2014-11-27
Are both hplip packages installed?   Go to the Ubuntu Software Center and type "hplip" in the search box.   When the results pop up, do you see that both packages (hplip and hplip-toolbox) are installed?   Note, IF a program/package is installed, you will see a green circle and check symbol over part of the icon  . . . install both packages if not already installed.

Then, open the System Settings app, and open the printer app.   If any printers show up, remove (uninstall) them.

Next, be sure the printer is on, and connected via usb cable, and restart your PC.

Reopen the Systems Settings, and then reopen the printer detection/installer app (NOT hplip or hplip-toolbox).    IF your printer doesn't show up, input a search on just "photosmart" and see what printers show up.   Find your model, and select it to do a reinstall.    At the end of the reinstall process, you should get a screen that will let do a test-page print.

BTW, when you install the hplip-toolbox, be sure the helper apps (xsan, simple scan, etc.) are also selected.   If they don't show on the screen, just search for those and install them.

---

