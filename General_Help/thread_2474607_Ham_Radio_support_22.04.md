---
title: "Ham Radio support 22.04"
date: 2022-05-03
forum: General Help
---

### Post by a_hippie on 2022-05-03
I've been monitoring #ubuntu-hams for the past week and that channel is completely abandoned :(

I upgraded to 22.04 last week and all went well until I started fldigi and noticed no CAT control.  Finally discovered /dev/ttyUSB0 is made, then fails, but continues to remain in /dev.  Some how, Ubuntu lost driver support for Silicon_labs serial/usb chips which are in current Kenwood rigs.

I downloaded ubuntu again, put it on thumb drive and verified failure with 22.04.  21.10 has full support, and current Mint has full support.  I'd love to cure this issue and could use some help guiding me in this effort.

Next, xastir aprs client absolutely crashes the desktop.  Doesn't matter if run as user or root.  Launch, crash.  Downloaded debs of old stable, crash, testing crash, unstable crash.  Bugger is, it happens so fast that I can't figure out why since it takes the terminal out with the desktop.  I run an aprs net every Monday and would really like to get xastir working.

Anyway, the CAT control is primary, I've moved xaster to my Rpi until I can restore functionality on ubuntu.  Need CAT for much of the software I use from js8call to WL2K.

I searched for specific ham help, but by gosh, there is nowhere I could find.  That is why I am resorting to "GENERAL HELP" on this forum.  Trying to find hams that understand our specific computer needs.

Tnx all, 73

Jaye ke6sls


PS:  good on qrz for contact.

---

### Post by HermanAB on 2022-05-04
Howdy, I am a non-ham ham - used to design radio stuff for a living and never bothered to register as a ham since I don’t transmit at home.  There is enough fun to be had receiving things.

In my experience it is best to install ham stuff on an old laptop or a low cost Raspberry Pi and once it is all working, do not ever update it, since updating can break everything - as you have found.

Another way is to make a virtual machine, but direct feedthrough of I/O is a hassle.

For best results, once you found  a distribution that works, download everything and make an installation server with all the sources - it is only about 15 GB for the whole kit and kaboodle.  Then you are independent.

---

### Post by a_hippie on 2022-05-04
Tnx for the feedback Herman.  You sound like you'd be a natural ham and I hope you seriously consider becoming licensed.

I still want to solve these issues.  More hams will be in this situation soon enough and it would be great if I could find a method to repair and pass this along to others finding themselves in this same pickle.

TU

Jaye

---

### Post by HermanAB on 2022-05-05
Well, there are two solutions: Install an older version of Ubuntu that works, or download the sources, recompile the broken applications and fix the bugs.  I am too busy with other stuff at the moment to recompile packages, so your options are limited.

---

### Post by a_hippie on 2022-05-05
Hello again Herman,

I'm looking for the third solution--resolving the issues with current this LTS release.

73
ke6sls

---

### Post by HermanAB on 2022-05-06
Well, your third solution requires downloading the  application source code and compiling it.

---

### Post by a_hippie on 2022-05-11
Finally resolved failure with the serial/usb device driver:

[https://ubuntuforums.org/showthread.php?t=2474936](https://ubuntuforums.org/showthread.php?t=2474936)

I hope I am stirring up some dust locating fellow hams here on this forum so we can find work-arounds for this LTS release.

Again, TU & 73

ke6sls

---

### Post by al-williams on 2022-05-31
A big thank you to Jaye.

I had a port connection problem using Mono 6.x from Ubuntu 22.04 to a RF Explorer 6G Ultra plus.

Logged a Support Call earlier with RF Explorer Support.

I stumbled on you fix tried it and it fixed my issue!!


There are other Hams out there .. !!

73 
Alan M7WLA

---

### Post by a_hippie on 2022-05-31
Alan,

Great to hear from you!  Glad to help.  Lots of problems with ham software and now looking at other distros :(

hamlibs appears very broken.  The dev for hamlibs haven't attempted to assist, so I'm stumped and bummed ...

Anyway. little by little.

73
j

---

### Post by David2009 on 2022-06-05
Congratulations!!!! And, thank you!!!!

73 de David AE4LH

---

### Post by HermanAB on 2022-06-06
Howdy,

The problem is that the old ham RF toys are generally very basic and decades behind the times.  The real ham action nowadays, is mostly done by non-hams.  See RTL-SDR ([https://www.rtl-sdr.com/](https://www.rtl-sdr.com/)), Satnogs ([https://satnogs.org/](https://satnogs.org/)) and many optical meteor detection systems ([https://www.cloudynights.com/topic/607632-diy-meteor-camera-system/](https://www.cloudynights.com/topic/607632-diy-meteor-camera-system/)) and ([https://allskycams.com/](https://allskycams.com/)) and another ([https://en.sci.hr/scientific-technological-projects/croatian-meteor-network/](https://en.sci.hr/scientific-technological-projects/croatian-meteor-network/)).  There are a plethora of RF projects going on that only need receive mode and which therefore doesn't need the ancient and kinda useless ham training.

---

