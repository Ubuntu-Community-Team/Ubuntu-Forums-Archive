---
title: "Printing Help, please"
date: 2024-05-16
forum: General Help
---

### Post by RangerK on 2024-05-16
[IMG]http://romanskaskiw.com/blog/wp-content/uploads/2024/05/Screenshot_2024-05-16_18-57-43.png[/IMG]

I've been working on this for a few days now, wasting SOOOOO much time.  I have made almost no progress and would appreciate any help I can get from you good people.

I have a Brother MFC-J1170DW injet printer.  When I bought it a couple of years ago, it worked right out of the box.  I recently went on a business trip, and returned, and now the printer won't work from by Ubuntu (Xubuntu, actually) laptop.  I can still print from my Android phone using the Brother app, but nothing works from my computer anymore.

Jobs get sent but stay on "Processing".  They'll stay there for an hour.

Things I've tried:

- Removing and adding the printer again, a million times.
- Removing and installing printer drivers.
- Installing the Linux printer driver (deb), and also running the Driver Install tool from Brother - [https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcj1170dw_us&os=128](https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfcj1170dw_us&os=128)   (When I ran it, it said that the drivers may become depreciated soon.)
- I did the previous step as part of following all the instructions here - [https://askubuntu.com/questions/636363/how-do-i-install-proprietary-drivers-for-my-brother-all-in-one-printer-scanner-f](https://askubuntu.com/questions/636363/how-do-i-install-proprietary-drivers-for-my-brother-all-in-one-printer-scanner-f)
- I also tried commenting out that AuthType and Reqire user lines from my cupsd.conf file as described here - [https://askubuntu.com/questions/1088858/printer-is-stuck-at-processing-status](https://askubuntu.com/questions/1088858/printer-is-stuck-at-processing-status)

All the steps seems to complete without a problem.  I determined and then selected the printers IP address and URI.   But the problem persists.  It just hangs.  I talked a couple of times to Brother but they said they don't do over the phone support for linux.

Any help would be appreciated.

---

### Post by RangerK on 2024-05-16
PS - usually, I just try to print a test page.  Sometimes I've also tried to print a document (libre office, or a web page).  The job just freezes in "Processing".

BTW, in the screenshot, you can see two printers.  I've tried this with both of them.  Interestingly, the one on the LEFT seems to appear automatically.  I keep deleting it and it keeps coming back.  I've tried printing with either one, though, and the result is the same.

Also, the Printer that appears automatically in my settings has Media size set to "Letter" instead of "A4".  I've tried printing both with changing it to A4, and leaving it as "Letter" but nothing seems to help.

---

### Post by RangerK on 2024-05-17
PPS - I dusted off an old laptop which also runs Xubuntu, and it's having the same issue.  So I suspect something in the updates broke printer compatibility.

---

### Post by oldfred on 2024-05-17
What version, flavor of Ubuntu?

My Brother Laser printed just works in 22.04 & 24.04.
In 22.04 I would get 3 printers and only one really worked.

[https://wiki.debian.org/CUPSDriverlessPrinting#ippoverusb](https://wiki.debian.org/CUPSDriverlessPrinting#ippoverusb)

If older Ubuntu is this the issue?
ippusbxd is decidedly sub-optimal. Even its author would support your removing it from your system. 
It has been replaced by ipp-usb in later editions of Ubuntu. 

And with video, I know installing a new driver conflicts with old driver. So older driver must be purged first.
If you have installed too many drivers from different sources, you may have conflicts.

---

### Post by RangerK on 2024-05-17
Hey,  Thanks for replying.  I'm using Xubuntu, which as I understand, is Ubuntu 22.04 with a different desktop.  The old laptop uses the same thing -- I started by running the standard update / upgrade to get the latest of everything.

The terms 'ippusbxd' and 'ipp-usb' are completely new to me.  (Is it relevant given that I'm connecting via wifi instead of USB?)

May I trouble you to refer me to some instruction for how to identify and remove all old drivers?  I'd love to stort of start again from a clean slate, but all the instructions / tutorials / advice I encounter seems to add a little something or change a little something to the configuration.  I feel like I have this accumulation of attempted fixes and I'm not sure whether or not I've done more harm that good.

---

### Post by oldfred on 2024-05-17
I have installed nothing from Brother. And do not think I installed anything with my Kubuntu.
It all just worked as soon as it saw printer. 

This shows a lot of info.
[http://localhost:60000/general/status.html](http://localhost:60000/general/status.html)
[http://localhost:631/admin](http://localhost:631/admin)

---

### Post by dragonfly41 on 2024-05-17
You write that printing stopped working after a business trip? Puzzling.

[I][COLOR=#000000]I can still print from my Android phone using the Brother app, but nothing works from my computer anymore.

[/COLOR][/I][COLOR=#000000](a) Can you try creating a new user login on your laptop to start a fresh environment?
(b) Can you print from LiveUSB?[/COLOR]

---

### Post by RangerK on 2024-05-26
oldfried, dragonfly41 - 

Thanks a lot for your responses.  I was sitting down to try printing via USB cable, and/or printing from a new user login.   . . . . and . . . . everything just worked from the old setup.  I suspect this all happened via sudo apt updates / upgrades.

Thanks for the responses.  I really appreciate them.  I love being a linux user, but the price of free software is hitting this sort of brick wall about once a year where I just get stuck.

all the best,
R

---

### Post by iamjiwjr on 2024-05-26
I downloaded the deb driver from Brother. That has consistently worked best for me on my HL-L2390DW laser printer.

---

### Post by currentshaft on 2024-05-26
asd

---

