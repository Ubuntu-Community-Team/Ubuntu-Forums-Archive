---
title: "Edit a PPD file"
date: 2019-02-14
forum: General Help
---

### Post by lennybruyninckx on 2019-02-14
Dear Ubuntu users,

I am using a Dymo LabelWriter 450 and it works on my Ubuntu wich is good but the driver does not support my labels I am using. The dropdown menu got only about 8 labels to choose at wich is silly if you have a labelprinter with many label formats. My question is: how can I add labels to this PPD file/driver? I have tried to find it in usr/share/cubs/model (wich is empty). usr/share/cubs/PPD nothing usefull there. No dymo.ppd foud so far.

I have a few printscreens to show you what i mean (unfortunatly Ubuntu does not make a printscreen if you have a drobdown menu opened). In the print screens you can see that I am able to select the dymo labelwriter driver and that this dymo.ppd file is on an location wich I tried to enter by just entering the path in my browser but no results so far.


I hope somebudy knows where the location is and how I can edit them to work with my multi purpose labels (art no. 11354) with these dimentions 3.2cm H * 5.7cm W

[ATTACH=CONFIG]282511[/ATTACH][ATTACH=CONFIG]282512[/ATTACH][ATTACH=CONFIG]282513[/ATTACH]

Many thanks!

Kind regards,
Lenny

---

### Post by him610 on 2019-02-14
Go to the website, [http://www.dymo.com/en-US/dymo-label-sdk-and-cups-drivers-for-linux-dymo-label-sdk-cups-linux-p--1]("http://www.dymo.com/en-US/dymo-label-sdk-and-cups-drivers-for-linux-dymo-label-sdk-cups-linux-p--1")
Download and extract DYMO Label SDK and CUPS Drivers for Linux, dymo-cups-drivers-1.4.0.tar.gz
It should extract it to directory (download directory)/dymo-cups-drivers-1.4.0.5 with a subdirectory, /ppd
Inside the ppd subdirectory, there will be many ppd files, you need to use the lw450.ppd file when you setup your printer in cups.
There many other labelwriter ppd files, make sure you choose the one that corresponds with your model.

Good luck.

---

### Post by lennybruyninckx on 2019-02-15
I have tried this as well but the PPD file it to old for my CUPS version. I have used this file and when I tried to print I got a message saying that the printing has been stopped. I am not in front of my computer but I know that this ile does not work as well as the other files with the same model number as my printer. The only working driver is from that PPD server. My idea is looking in that file and compare all the data needed to get that PPD file working wich is comming from the SDK package

---

### Post by CatKiller on 2019-02-15
PPD files are text files that specify the attributes of a printer. Any text editor could edit them. Some of the syntax is described [here](https://www.cups.org/doc/spec-ppd.html).

I have no idea if you'll be able to achieve what you want by editing the PPD file.

---

### Post by lennybruyninckx on 2019-02-15
I want to edit my current PPD file. The issue: Where is that PPD file located?
I choosed my working driver from the server by clicking choose your driver in the printing settings. I need that file to look in to it so I can add my labels wich I am using.

---

### Post by CatKiller on 2019-02-15
Mine seems to be in /etc/cups/ppd/ but a **locate .ppd** should help you find it.

---

