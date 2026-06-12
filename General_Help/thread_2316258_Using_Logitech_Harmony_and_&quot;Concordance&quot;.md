---
title: "Using Logitech Harmony and &quot;Concordance&quot;"
date: 2016-03-06
forum: General Help
---

### Post by jlh68 on 2016-03-06
I found an application in the Ubuntu Software Center named "Concordance" and it is a CLI  application to program the Harmony remote.  [https://github.com/jaymzh/concordance](https://github.com/jaymzh/concordance)

This CLI application is supposed to get me connected to the Harmony remote for upgrades.  I have a Logitech Harmony 650 universal remote and it is updated either with Win OS, or Mac OSX OS and not supported by Linux.
I can use Wine and get the Harmony application so that I can change my settings but I can not get the remote to connect with my Ubuntu OS.  

I cannot get Concordance to open the config.EZHex file.  I am not sure of my CLI capabilities. 

I am using Ubuntu 15.10, and I have a Harmony model 650 remote.  I also am using WINE and have Concordance  installed.  I have the Harmony App version 7.7.0.  When I go to [Http://members.harmonyremote.com/EasyZapper/](Http://members.harmonyremote.com/EasyZapper/) it will update the browser interface to harmony verson 7.8.0.

I cannot get the CLI command concordance EZHex to open.

Question 1. is am I doing the Command Line right?  Question two is does has any one else used this application and could help me?

---

### Post by jlh68 on 2016-03-06
OK my Linux friends, I found a solution. :)   I found a GUI in the Ubuntu Software Center called _Congruity_ that with Concordance and the harmony web site.  First three trys were unsucessful.  Got on the Harmony Support  and for a way to reboot the remote as it was not being found by Congruity+Concordance app.  Took the remote batteries out, reconnected and started again.  This time the remote connected to my laptop and the apps did their thing.   So now I can update my Logitech Harmony 650 universal remote with my Ubuntu  OS  laptop.  I am assuming that WINE was used in this but really not sure it was at all.

That only leaves my TomTom GPS needing Windoze or Mac for upgrades. :P The Harmony 650 can now be done with Linux.

---

### Post by jean noel on 2016-11-20
Hi, I have been trying to use Ubuntu to program my 650 remote fro a long time. Did you install wine? BTW I am using 16.04, wit a Win 7 partition, only for Harmony remote software.
Thanks 
jean Noel

---

### Post by jlh68 on 2016-11-20
[https://sourceforge.net/projects/congruity/](https://sourceforge.net/projects/congruity/)

You can down load from the above web site. Both Congruity and Concordance are on the site.  Concordance is in the right hand panel.

---

### Post by marawuti on 2016-11-29
I'm kind of going at this bass ackwards so bare with me.

I have the Harmony 650 configured fine on a Windows 10 via the MyHarmony App; however, I'd like to be able to do as you have on my linux box.
But it appears that somewhere along the way, I think it was with your Wine efforts, you produced a config.EZhex file.
Is there a way to cause concordance to initialize a config.EZhex file or is some other way of getting a usable / initialized config file?

---

