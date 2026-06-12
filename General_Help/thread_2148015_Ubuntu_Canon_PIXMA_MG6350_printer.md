---
title: "Ubuntu Canon PIXMA MG6350 printer"
date: 2013-05-23
forum: General Help
---

### Post by Klapacjusz on 2013-05-23
Hi, I recently switched to Ubuntu at home (was using it more then 2 years at work), and in general I'm very happy. 
Although there is a slight problem with a printer.

I'm using **Canon MG6350** (wifi, multifunction, 6 inks) and I'm using Canon's official drivers. Which works well, but:


[LIST]
[*]I cannot switch color mode to CMYK (and red colour is more of an orange on ubuntu test page)
[*]I cannot select resolution other than 600dpi
[*]No updates of ink levels
[/LIST]

Yesterday I've used Cups + Gutenprint builtin drivers but for MG6200 (no MG6300 drivers). I can see ink levels there, and select CMYK (and others), and select higher dpi, but although printer seems to receive commands (*receiving data* message is displayed on LCD), nothing is printed. Funny thing is that it does after-print beep, but nothing is printed, it just is processing something, and then beeps. 

So i guess something is wrong with the driver.

I've tried manually to add CMYK option to ppd file (in /etc/cups/ppd/), after making backup of course, but it doesn't seem to work (window properties crashes). 

I have few questions:
[LIST=1]
[*]Can I expect cups+gutenprint support of my printer in nearest future?
[*]Are there other drivers I could use?
[*]Is my problem with color might have something to do with Color Mode: RGB set (and no option to choose CMYK)
[*]What about color profile ICC file - can it help to solve orange problem (I found some various ICC files on windows driver CD, and added them in settings but I'm not sure how, or if they work)
[/LIST]

---

### Post by pdc on 2013-05-23
1) to change the resolution, this thread

[https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/PIXMA](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/PIXMA)

talks of editing the ppd file
_______________________________

2) I notice you are using the gutenprint driver: Canon supply drivers

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100469202.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100469202.html) the packages comes down as cnijfilter-mg6300series-3.80-1-deb.tar.gz
so the commands to install would be:
cd Downloads
tar -zxvf cnijfilter-mg6300series-3.80-1-deb.tar.gz
cd cnijfilter-mg6300series-3.80-1-deb
sudo ./install.sh
sudo service cups restart
_________________________________________-

3) ink levels
a recent thread in Ubuntu
[http://ubuntuforums.org/showthread.php?t=2145083&page=2&highlight=inq](http://ubuntuforums.org/showthread.php?t=2145083&page=2&highlight=inq)
covered the install of [COLOR="#0000FF"]inq[/COLOR] that should measure ink levels and show them graphically; I have also used [COLOR="#0000FF"]ink[/COLOR] from a command line; it works well too;
inq needs a host of dependencies installed before you install inq: see post #13 for those and see post #3 of the above thread for where you get inq from 

_____________________________________________

4) if you **_install the Canon drivers_**, they offer a utility 

> [COLOR="#FF0000"]cngpij -P MG6300USB[/COLOR]

that you initially run from CLI that allows you to set various things up; and can be made into a launcher for repeated use

---

### Post by Klapacjusz on 2013-05-24
> **pdc said:**
> 1) to change the resolution, this thread

[https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/PIXMA](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters/PIXMA)



thx, this is helpful 

> **pdc said:**
> 
2) I notice you are using the gutenprint driver: Canon supply drivers

I've mentioned that at first I used official drivers. Now I have the same printer twice with different drivers - official and Guten.

> **pdc said:**
> 
3) ink levels
Gutenprint driver detects ink levels correctly. If I can find section in guten's ppd file and copy it to official PPD file, and then restart CUPS can It work??


> **pdc said:**
> 
4) if you **_install the Canon drivers_**, they offer a utility 


looked fine, but unfortunately I receive: ERROR: The specified printer is not supported.

---

### Post by pdc on 2013-05-24
from the 6300 guide, I see the command for the 6300 is different from that of our 3100 series:

see thumbnail

 it is 

> [COLOR="#FF0000"]cngpijmnt MG6300[/COLOR]

as you are interested in altering settings, can I recommend the Canon guide

[http://support-asia.canon-asia.com/contents/ASIA/EN/0300932401.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0300932401.html)

it comes down as [COLOR="#008000"]guide-pd-3.80-1_en.tar.gz
[/COLOR]
If you save in your Downloads folder; then right-click; open with archive manager; save to ..Desktop?

Open the guide; look for guide_index.htm and it should open Firefox; you should find things of value

> [COLOR="#8B4513"]If I can find section in guten's ppd file and copy it to official PPD file, and then restart CUPS can It work??[/COLOR]

You can but give it a whirl and see!!

---

