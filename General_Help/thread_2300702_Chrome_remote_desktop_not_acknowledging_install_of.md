---
title: "Chrome remote desktop not acknowledging install of their software`"
date: 2015-10-27
forum: General Help
---

### Post by mileshamilton on 2015-10-27
Good evening fellow Linux uxers. If you care to read my background info continue reading, if not, skip to the -----. I'm the type of person who can't just leave things well enough alone. I would rather take the hard way to a solution and have a cobbled together way of doing something while managing to learn a thing or two than just have an easy turnkey solution given to me that I don't understand. A few days ago I decided to run my trading software from home to minimize my downtime while trading/travelling. The obvious/easy way to do this is go to best buy/newegg/walmart and buy an el cheapo computer and just leave it on with a remote desktop client running. Instead I decided to pull out my old PC tower from 2003, install Linux on it, and run my trading software in WINE as I've had good luck with Ubuntu and WINE I thought this the obvious route. Unfortunately I miscalculated by expecting my old tower to be capable of running Ubuntu at a reasonable speed. It will run, just SUUUUUUUUper slow. This caused me to look into lower performance alternatives. After much deliberation I settled on Lubuntu. Let me tell you now, this whole process has been long with many many small steps and several deliveries from newegg for adapters etc coming in the mail for me. Tonight I got Lubuntu up and running. It looks great BTW. My plan is to run the Remote Desktop Extension for Chrome on my tower so I can access it from my cellphone throughout the day. I know the cellphone/windows part of this setup works because I am successfully using this same setup with my work laptop to my cellphone. The Lubuntu side is causing me problems.

-----After installing Lubuntu and getting it updated I installed Chromium (I've found it is a little resource intensive but not too bad). After getting Chromium working I downloaded and installed the Remote Desktop Connection app for Chrome. So far it is working. The issue I am coming across is when you are setting up the app, you have to download their RDC Host software. The app waits for you to download it and install. Now when I put it on my work laptop, after it was done installing the rest of the app install process started back up automatically. On Lubuntu, this does not seem to be the case. I tried installing from the default run as option, I also tried downloading and installing via command line to no avail. After checking through the forums I thought maybe it was because Lubuntu doesn't come packaged with the ability to remote share. I downloaded vino and adjusted the preferences but this didn't seem to help. Whatever I try, nothing seems to get that installer past the waiting for affirmation that I installed the host software. Does anyone have any tips/ideas you could help me out with in advance? 

Your help is much appreciated!!

---

### Post by Oyvind_Overby on 2016-06-05
After installing Ubuntu 1604 fresh (and before launching Chrome browser (v51) first time), I installed the CRD host and it complained about missing dependencies. so I ran 'apt-get -f install' and then reinstalled the CRD host.
Then I launched Chrome browser, logged in and installed the CRD extension from app store. It automatically detected that the host file was installed and running and could I go straight to 'Enable Remote control'.
But I too have a problem. Remote access works fine, but remote desktop just gives the error 'Invalid access key'.  The log shows PAM authentication failed.

---

