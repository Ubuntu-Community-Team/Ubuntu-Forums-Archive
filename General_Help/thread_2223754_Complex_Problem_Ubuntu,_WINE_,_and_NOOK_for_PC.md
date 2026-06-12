---
title: "Complex Problem: Ubuntu, WINE , and NOOK for PC"
date: 2014-05-12
forum: General Help
---

### Post by deamon_knight on 2014-05-12
Well, I'm trying to move all my computing over to Ubuntu but I'm running into a few hurdles. I have some eBooks from Barnes and Noble. With B&Ns "Nook for PC" app I can download the ePub files and read them on my PC offline, and import them into my calibre library. I'm not sure how I can do this from Ubuntu. I'm running Lubuntu 14.04 64bit.

I have downloaded WINE, and so I can install the Latest version of Nook for PC, but I cannot log in, it fails with an "error 1025". Some quick googling suggests this is a Internet Explorer cookie problem:

[http://bookclubs.barnesandnoble.com/t5/NOOK-Client-App-Support-iOS/FIXED-Nook-for-PC-login-1025-error/td-p/884812]("http://bookclubs.barnesandnoble.com/t5/NOOK-Client-App-Support-iOS/FIXED-Nook-for-PC-login-1025-error/td-p/884812")

I've installed winetricks vcrun2009, and I tried to install winetricks ie6 to see if I could manage "IE cookies" in that way, but its says ie6 wont install on my architecture. winetricks ie7 works, but Nook for PC still gives the same error.

Any ideas on how I can get this working?

Thanks

---

### Post by squakie on 2014-05-14
You can't access USB devices with Wine.  If you plug the data cable into the Nook and then into the PC, does a new device show in the file manager?

  Try this: 
unplug the Nook from the PC 
 plug the Nook in to the PC
  lsusb > ~/dwelsusb.txt
 cat /var/log/syslog | tail -n 30 > dwelog.txt  

Post back here attaching these 2 files from your home folder:  dwelsusb.txt and dwelog.txt.  The idea is that hopefully it will show as an accessable mass storage device and you can just copy the epubs off of it, just as is done with Kindles and other such devices.

---

### Post by deamon_knight on 2014-05-14
Thanks Squakie, but the problem isn't connecting my Nook tablet device to my system, its getting the "Nook for PC" application to run and allow me to login so I can read my B&N books on my system.

---

### Post by caver12 on 2014-05-14
Look in synaptic for gmtp see if that helps. it's not installed by default.

---

### Post by squakie on 2014-05-16
Is there a link to download that software somewhere?  I've got an old Nook color - currently running Android 4.2.2 - but I could still just try to get the app working.  No guarantees - it will need to be outside of Wine.  There is a package you have to pay for but does much much more that Wine ever will - I think it's called Crossover - but it's been a few years since I had it so I could be wrong on the name.

---

### Post by squakie on 2014-05-16
Okay, I installed wine and installed nook for pc, and i get the same error trying to login.  I'll do some investigating and see if I can figure it out.  I'm no expert but I'll try and in the mean time hope someone else comes up with something.

---

### Post by squakie on 2014-05-16
I did find [this]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=20818&iTestingId=60612"), which indicates it worked in 12.04.  don't know what happened.  i also noticed it gives a version number for reader app - perhaps we need to find a download for that version.  I'll keep trying.....

---

### Post by squakie on 2014-05-17
This error isn't limited to the app in wine.  searching the bn support tforums i found all kinds of these problems from all kinds of Windows versions from all kinds of dates.  some say to completely enable cookies in your browser doesn't need to be ie.  tried that but no change.

---

### Post by squakie on 2014-05-17
I also just found out that the version that I downloaded is for Windows 8 - the one for previous versions wasn't listed and according to their forums support and downloads for those versions was discontinued last year and only the versions for Windows 8 is available.  I did try setting my Wine to Windows 8 but still get the error.

I believe about the only way we might get this to work is to first start with an older version that did work with Windows XP.  Do you have such a thing or did you also download it recently?

---

### Post by squakie on 2014-05-17
This is odd - it let me create a new account from the app, but after I signed out it won't let me sign back in - gives the same error!

---

### Post by deamon_knight on 2014-05-18
Yea, I think I'm dealing with two problems, the log in problem with Nook for PC, which appears related to cookies in some way, and running a 32bit WINE prefix. How are you installing Nook for PC? Have you tried running winetricks and installing from that list. The "Nook forPC" listed there seems to be an earlier version; and I supposed it was maintained for compatability with WINE in some way? Not sure here.

---

### Post by squakie on 2014-05-18
The cookies thing I *think* may be a red herring.  I sat this because when I select things in Nook for PC that require a browser it opens Firefox because it is my default browser.  So 1st of all I don't belive that IE is a requirement.  Enabling all cookies doesn't seem to matter.  I'll try the winetricks thing again and see what happens.  32-bit shouldn't really make any difference.  I'm running 64=bit Ubuntu, but everything still loaded and runs.  I suspect this error is actually from the B&N servers.  I've read in some Nook related forums that they changed their database and people have beeb having problems since.  They no longer support or have a Windows download except for Windows 8.  The forums seem to indicate the database change happened for that.  This would mean the old software would no longer work, and I think the version may be sent for log on, and that's why it's being rejected.

I'll keep plugging away.

---

### Post by squakie on 2014-05-18
OK, tried the Winetricks thing.  Yes, it shows it as an older version, but it appears it goes to B&N downloads - which it the newest (and only) release for Windows.

I suspect that if I could figure out how to trace traffic to-from the Nook for PC application when trying to logon that the error message is coming from their servers.  From there, I'm not really sure what to try.

---

### Post by squakie on 2014-05-20
Tried Wine config to change to Windows 8 - still no good.  I'm thinking we may be out of luck here, and I suspect it's B&N's problem.

---

### Post by deamon_knight on 2014-05-23
Yea, I'm really not sure how to troubleshoot further. The "The Daily" section of the Nook For PC application sems to be getting stuff from B&N servers. Since windows users are also expericing the problem I would think it was a network configuration matter, but some users are saying changing IE Cookies solved the problem. I wouldn't surprise me if Nook for PC was really invoking IE in some way, but I am baffled.

---

### Post by fwrun2011 on 2015-02-25
Well, here it is 9 months later and B&N still hasn't got a reader that will run on Ubuntu 14.04.
I have tried everything - installed Wine, Q4Wine, and all that I can find with the name wine in the software center.
I get the same error - 1025. I am also running Ubuntu 14.04 64-bit.
I got on chat with B&N and he told me that I probably needed to run the program on Windows. Sure - that works fine. I can download my book (I bought only one, thank you) on Windows, but it won't do me any good, since my book is "A Practical Guide To Ubuntu Linux 4th edition" by Mark Sobell - I need the book to be available while I am running Ubuntu!!

I am probably going to contact B&N and get a refund. But I still have one other option - I have a 2nd box which runs Windows XP SP3, and if I can install the reader on that machine, and it looks ok on the small monitor (15" older LCD) then I can boot up that PC when I want to study Ubuntu. Only problem there is that the monitor is not as clear as my main one, and I need to have two mouses to navigate through the book and Ubuntu.
I wonder whether B&N will give me a refund (the guy I chatted with says that will not be a problem), and let me keep the copy I already downloaded to Windows. I wouldn't feel at all bad about that, since I have gone through so much trouble over this. And the only reason I purchased the book from them is that it was about $11 cheaper than buying it on Amazon Kindle - and I can read Kindle books on my Ubuntu system because they have the Cloud Reader!!

Or perhaps I will just eat the $11 and buy the book from Amazon. Less hastle, no need to boot up another pc just to read this one book.

FW

---

