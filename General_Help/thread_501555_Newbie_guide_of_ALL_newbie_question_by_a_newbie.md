---
title: "Newbie guide of ALL newbie question by a newbie"
date: 2007-07-15
forum: General Help
---

### Post by yungwunn911 on 2007-07-15
Hey All, 

So, i just installed ubuntu 7.xx  on my old AMD athlon PC. It has about 384 mb RAM on it. 

There is a slight lag on all process with this OS, any way to figure out why and make it run optimally? 


Also, what package are worth installing on this bone stock ubunto 7? I hear that KDE is a must, some background info on it would be great.

-mike

---

### Post by starsky on 2007-07-15
Hi there :)
welcome to ubuntu :)

In that machine specs, i'd suggest you use XFCE Window manager.

[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

after doing the above said instructions,
```


$ sudo apt-get install xfce4-goodies


```

post back :)

HTH

---

### Post by merlinus on 2007-07-15
What is included with 
xfce4-goodies

Thanks!

-merlin

---

### Post by yungwunn911 on 2007-07-15
> **merlinus said:**
> What is included with 
xfce4-goodies

Thanks!

-merlin

i'd like to know as well. What will be taken away? can i come back to ubuntu later?

-mike

---

### Post by Nythain on 2007-07-15
The "Goodies for Xfce" project includes additional software and artwork that are related to the Xfce desktop, but not part of the official release. 
 This package will install the following Xfce4 related plugins: 
  * Extra artwork
  * Battery levels monitor
  * Clipboard history
  * Disk performance display
  * Filesystem monitor
  * Mini command-line
  * Network load monitor
  * Sticky notes
  * Sensors monitor
  * Smartbookmark control
  * System load monitor
  * Command line with history (verve)
  * Weather monitor
  * Wireless monitor
  * Gnome applet plugin (xfapplet)
  * Xmms plugin
 This is a meta-package to ease upgrades, installations, and provide a consistent upgrade path from previous versions. It can safely be removed with no ill effects.

---

### Post by sloggerkhan on 2007-07-15
I don't know what is included with xfce4-goodies, I'd have expected the metapackage to be xfce4-desktop, but in any case you will be able to use the gnome desktop still. The gdm login manager should remain in place, and if you click the SESSIONS option found somewhere on it, there will be a gnome session and a xfce session so that you can choose which one.

---

### Post by starsky on 2007-07-15
yup. sloggerkhan is correct. GNOME will NOT be affected.

HTH and enjoy Ubuntu :)

---

### Post by yungwunn911 on 2007-07-15
I thought this package was suppose to make the computer run smoother...

its sounds like this package only adds things to the existing Ubuntu OS, are the things its adding smaller less complicated files to make the os run quicker then?

will adding that prompt in the command automattically install eveyrthing and nothing else need to be done?

---

### Post by sloggerkhan on 2007-07-15
The way it works is that the dektop environment is loaded based on the GDM session script from the login manager. For xfce, it should load xfce stuff and not gnome stuff, resulting in less intensive use of the system. The gnome environment will still take up space on your hard disk, but if you start up and log into xfce, gnome processes probably shouldn't be running.

So far as installing foes, you can just install from command prompt and let it go. Don't need to do anything else. You will need internet for it to dowload.

---

### Post by yungwunn911 on 2007-07-15
Thanks very much. The xfce  works GREAT and much much smoother than the orignal ubuntu i had. I actually like the desktop alittle better now! Going to check for more questions about this OS and will post in here, so that any other new people may refer. 

my next task is to install my printer!

-mike

ps, it seems that the spell check feature is disabled now. As i write and misspell things are not underlined red. Anyone?

---

### Post by metallicamaster3 on 2007-07-15
or just using Xfce altogether instead of Gnome may be another excellent. Using Xubuntu, you will get the more performance out of your system.

---

### Post by sloggerkhan on 2007-07-16
Well, if it's in firefox, you may need to right click and hit the checkmark that says spell check this field.

---

### Post by NewToU-buntu on 2007-10-13
I downloaded 7.04 and when I load using the disk I get an error message on my 19" dell monitor saying "can't display this resolution, optimal resolution 1280x1024" then the screen goes blank and loads up Ubuntu in a fuzzy format.  When I install it reboots and I get the error message but that is it, no Ubuntu after.  I tried installing with the driver cd for the video card, It didn't work, Tried the driver cd for the monitor, No luck.  I looked up a help on the web and it said to change the xorg.conf file.  I changed the file to include "Monitor - Horizontalsync 30-95 and verticalscan 50-160 and the display modes to include 1280x1024.  This didn't work.
I tried installing the ubuntu and then loading the drivers from the cds.  That didn't work.  I tried loading the drivers from ATI manually, No joy.
I am using a P4 3.0Ghz with an ATI Radeon 9600xp and a dell E196fp monitor.
Any suggestions?
Oh and the monitor section of the xorg.conf file just says "generic monitor".

---

### Post by averagebeatboy on 2007-10-31
Hi,

I am attempting to use Wine to run Quake II.  I do not think this is a Wine question, I hope not anyways.  The Wine Version I am using is 0.9.48 and it is not giving me any problems thanks to Frank's Wine Page.  My problem lies with my CD-ROM, I believe.  

When I put the Quake II disc into the drive everything is fine and an icon comes up saying Quake II.  Because of my attempts to install Quake II via Wine (Understand that I have never used a data disc under Ubuntu, with the exception, of course, of Linux discs). My discs are always music discs and they never have given me a problem.

Since Quake II was not working as Frank's page assured me it would (just joking, Frank) I went into the properties of the CD-ROM disc clicked on the **Drive Tab** to find to my amazement that under **REMOVABLE **it tells me that my CD-ROM is Yes, Removable and Ejectable!  I am wondering if that is why I am having a nightmare trying to install Quake II?

If Ubuntu "Gutsy Ribbon 7.10" is reporting that my CD_ROM is an ejectable device and removable does this mean that I need to mount the CD-ROM before it will obey anything Wine is telling it to do?

Wine tells me under the Drive Tab that C: /media/cdrom/ is there and also E: /media/cdrom0 is there, but I only have one CD-ROM.

Can anyone lend a hand with this perplexing yet (for me) interesting "problem"?

Best,

Averagebeatboy (Newbie)

---

