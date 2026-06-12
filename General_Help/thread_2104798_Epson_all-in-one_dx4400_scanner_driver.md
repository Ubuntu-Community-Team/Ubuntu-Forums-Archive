---
title: "Epson all-in-one dx4400 scanner driver"
date: 2013-01-14
forum: General Help
---

### Post by tedd.aiwa on 2013-01-14
Hi there, I have  an **Epson DX4400 printer/scanner  **running on Kubuntu 12.10
The printer does work (with Linux drivers I suppose), but the scanner doesn't. 
I tried to follow these steps: [http://ubuntuforums.org/showthread.php?t=1534230](http://ubuntuforums.org/showthread.php?t=1534230) but nothing happened. I take the same answers as "balta" on the above thread.
Is there anything else I can do to make my scanner work?
Thanx in advance

---

### Post by pdc on 2013-01-17
so if we just check what you have installed:

if you copy and paste

> [COLOR="Red"]sudo dpkg -l | grep iscan[/COLOR]
You don't say if you have 32bit or 64bit ..I assume 32bit...

If I just go over what one should presumably do

from here [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

then one gets to here

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=20920&DSCCHK=1f66541498e19eb24ca3c111022918affda59631](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=20920&DSCCHK=1f66541498e19eb24ca3c111022918affda59631)

and installs

1) [COLOR="SeaGreen"]iscan-data_1.20.0-1_all.deb[/COLOR]

then 

2) [COLOR="SeaGreen"]iscan_2.29.1-5~usb0.1.ltdl7_i386.deb
[/COLOR]
and from here

[http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

3) install [COLOR="SeaGreen"]iscan-plugin-cx4400_2.1.3-1_i386.deb[/COLOR]

.........and that's what you did?

.......and the device is connected by usb cable without using a USB hub to a standalone computer?

---

### Post by tedd.aiwa on 2013-01-17
Thanks for the immediate response. Yes I have 32 bit and I tried all the steps you gave me in the exact order but still the same problem:sad:
If you know anything else about it please help.
Thanks again

---

### Post by pdc on 2013-01-17
I think you need to delete all ..and start again ..

....and copy and paste any error messages you get .....

I would use synaptic (Package manager) and remove all the iscan entries;

then begin again..

iscandata; then specific programme; then on the home stretch, plug-in

and if errors message: do not proceed further and paste here what you get as error messages:

are you willing to do that?

---

### Post by tedd.aiwa on 2013-01-17
I'm certainly willing to do so, just as a new user I'll need some help from you.
How do I delete everything I did so far?

---

### Post by pdc on 2013-01-17
you have kubuntu: there should be what is called "package manager" there ..in Administration it is called synaptic package manager: if you use the "search" option in your Menu and type something like package..it should show it to you: if you open it up, it should be like the thumbnail I enclose called synaptic:

you can see I typed cnij searching for the canon drivers I have and you can see them listed......

so you would left-click on the green button for each of the iscan entries, and select for complete removal

......click on the APPLY button on the top menu line...otherwise it all just good intentions!! 

......and I guess install by going to your Downloads directory; and right-clicking on each entry in turn: and select to install with gdebi installer; so the system knows you have them installed......

data; then specific then to plug-in

post back if I have not been clear enough so far

---

### Post by tedd.aiwa on 2013-01-17
&#913;fter a thorough search in the installed software (in Muon) there aren't any "iscan entries".
I searched also with synaptic,the same no iscan entries found...
Isn't it strange?

---

### Post by pdc on 2013-01-18
I can't have subscribed to this thread as I did not note your reply..

well........ 

go to the Epson site and download the 3 things you need; as you click to download, gdebi installer should offer to install; let's see how it goes;

if you need pointers where to go, let me know

---

### Post by tedd.aiwa on 2013-01-21
The problem is SOLVED!!! I just used "gdebi-kde" (instead of "muon") for installing the 3 files and it's all done. Thanx again, your help was much appreciated.:lolflag:

---

