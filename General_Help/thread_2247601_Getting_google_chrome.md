---
title: "Getting google chrome"
date: 2014-10-09
forum: General Help
---

### Post by justin45 on 2014-10-09
I'm using the 64 bit versin of ubuntu linux, version 14.04.1. I have a dell laptop. I make a DVD disc of ubuntu linux. I boot the laptop off of the disk and choose try ubuntu linux. By default, google chrome isn't installed with linux. I would use firefox, but firefox doesn't include flash and there are a lot of websites that use flash.
I go to google.com and google in google chrome. I click on the first link that shows up. The website attempts to load, but I get a blank page and then my screen just turns black. At this point, I have to do a hard reboot.

What is going on? In the past, I would go to the google chrome website, download google chrome and then install google chrome. I never had any problems before.

Is there a way that I can get google chrome for ubuntu linux or is there another browser that I can use that has flash built in?

---

### Post by kurja on 2014-10-09
Do you need to run Chrome on a live cd session?

Can't you just use [google's ppa]("http://www.ubuntuupdates.org/ppa/google_chrome") to install chrome, why are you heading to some website to download it?

Or if you just want the flash, get *flashplugin-installer *from software center and use firefox, did that not work for you?

---

### Post by Mike_Walsh on 2014-10-09
Hi.

You would probably find it just as easy to go to the Software Centre and install Chromium-browser. This is the open-source version of Chrome, which is where all the Chrome development work is done.

Like Chrome, it too has the pepperflash plugin included as standard; so you can use flashplayer 'out-of-the-box'.

Or, as kurja has suggested, obtain the flashplugin-installer for Firefox. It, too, is a very good browser. Try it; you might be surprised!

Regards,

Mike.

---

### Post by kc1di on 2014-10-09
[this page]("http://www.omgubuntu.co.uk/2014/06/install-pepper-flash-chromium-ubuntu-14-04") will tell you how to install pepper-flash.  It is newer than flash plugin. 

I've had no problem with google-chrome here when installed from their web site. or the PPA  again [here's a page]("http://askubuntu.com/questions/510056/how-to-install-google-chrome-on-ubuntu-14-04") that tells you how to do it. 
Also I believe from your description your running in live mode.  Even if you install chrome in live mode it will be lost the next time you reboot. 
good Luck

---

### Post by vasa1 on 2014-10-09
> **kurja said:**
> Do you need to run Chrome on a live cd session?
...
^^^ This. I don't think what you're trying to do is possible especially with a DVD.

---

### Post by justin45 on 2014-10-09
I tried the flash plugin installer and that works for me.

I don't know a lot about linux so I practice skills from time to time. In the past, at least for me, it's possible to install chrome from google.com/chrome. Now it's not possible.

I know that everything will be lost when I either power down my system or restart it.

Thanks a lot for everyone's advice.

---

### Post by yancek on 2014-10-09
I downloaded and installed google-chrome beta from their site two weeks ago without problems, the link below.  It also downloads from the stable, so there's something else going on:

[https://www.google.com/intl/en/chrome/browser/beta.html](https://www.google.com/intl/en/chrome/browser/beta.html)

[https://www.google.com/chrome/](https://www.google.com/chrome/)

---

### Post by kc1di on 2014-10-10
Hi again Justin45, 

I would advise that you find someway to do a real install of Ubuntu- then practice as there is a lot you simply can not do with the Live DVD.  The problem with installing chrome may be just that the DVD has not allowed enough temporary disk space to accommodate the file. 

also there is a way using a USB drive you can make the live session persistent you can find the information   [here.]("https://help.ubuntu.com/community/LiveCD/Persistence") 
That way you at least would not loose all your work every time you re-boot. 
Good Luck and hope you enjoy Ubuntu :)

---

