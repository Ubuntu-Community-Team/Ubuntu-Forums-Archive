---
title: "Dell Mini 1012: High temp issue"
date: 2014-10-15
forum: General Help
---

### Post by trevor18 on 2014-10-15
Hi new to ubuntu, finally making a switch from windows. 

Decided to try ubuntu 12.04 LTS since it is still supported and im using a low hardware system.

Setup is 
Dell Mini 1012
1.6 Intel atom n450 
2gb Ram
Broadcom Crystal Hd card
WD 160gb 7200rpm hdd
1366x768 display

I fornatted the hdd and copied the ubuntu 12.04LTS iso to a usb flash drive from another pc. Install went perfect and everything seems to function as normal display,wifi,sound etc. Once connected to the internet it had 100s of updates. Everything up to date and installed in under an hour. Boot times are around 30 seconds. Web pages load fine.

Problem or concern i have is the cpu temp which sometime leads to the system bogging. Past few days ive ran it a few hours at a time and it hasnt overheat. But at idle the cpu temp is 60-70 degrees celcius. At first start the temp reads 32 and gradually increases from there. Just browsing firefox it runs 70-75 and when you play a video it will get in the high 80s. 100 is the rated max. This is a fanless netbook but when i previously ran windows it didnt have this issue.

It is making me nervous to stream College football games on for extended periods. Plus it makes the outside case temps HOT.
Ive searched for solutions and tried updating and installing several different things in terminal with no signs of change. 


Any ideas or would a switch to something like xubuntu, lubuntu work better? Thanks for any help.

---

### Post by trevor18 on 2014-10-16
Any thoughts?

---

### Post by coffeecat on 2014-10-16
> **trevor18 said:**
> Any thoughts?

I'll try. :)

I wonder...

> **trevor18 said:**
> 
1.6 Intel atom n450 

According to the Intel site, that processor contains the integrated graphics. if you are running the Unity version of Ubuntu, it uses compiz which is fairly graphics intensive. That could be the problem, and...

> **trevor18 said:**
> would a switch to something like xubuntu, lubuntu work better?

... is worth considering. Both of those are less demanding on the graphics and CPU. Rather than commit yourself to re-installing, I suggest you create a live USB with persistence for either or both. That way you could run Xubuntu and/or Lubuntu live befoer you commit yourself and you would also be able to install whatever you need to test it, such as video codecs and whatever you are using to monitor CPU temperature. You can create live USBs with the app startup disk creator which should be already installed in your Ubuntu 12.04.

The other option would be to install the respective desktops for Xubuntu and Lubuntu in your current installation and choose whichever you wish to test at the login screen.

---

### Post by trevor18 on 2014-10-16
Thanks for your reply. And yes it does carry integrated graphics and i think the broadcom card is for hd videos.  I assume i am running unity since i havent tweaked it to much, Is there a way to see what hardware is utilizing the cpu to tell if maybe thats the issue? Im using Xsensors to read the temp. 

Im not against making a switch just dont want to take that time if their is a more simple fix.

---

### Post by Michael_McKenney on 2014-10-16
I would check your CPU and chassis fans.  I usually replace them every 3-5 years.  Upgrade your BIOS on the motherboard.  I had one board with a bad BIOS rev that misread the temp sensors.

---

### Post by trevor18 on 2014-10-16
This computer was only used for a year or so since new, hardware is fine. Doesnt have fans, which i stated in my post. The temp is a correct reading. When i measure the external case temps with infared at 120ish degrees farenheit that would equal my 60-75 core temps in celcius. 

Everything works perfect in ubuntu just not happy with the constant cpu temp of 60-70 degrees under any normal use.

---

### Post by trevor18 on 2014-10-16
So i put xubuntu on a usb to try. Running the live version everything works with it and it does seem a little quicker. Installed Xsensors and Cpu temp was still idling around 60 and got up to 70 degrees. With ubuntu it does heat up more and alot quicker.  Not sure if this is a driver fault or if ubuntu just runs like this with my setup. May try linux mint next as i hear good things with it as well.

---

### Post by tgalati4 on 2014-10-16
Ohio State has a decent shot at a Bowl Game.

Oh, has your computer been dropped at all?  Any cracked corners?  Sounds like your heatsink has become dislodged.  On a fanless system, proper heatsink pressure is critical.

Only way to tell is to open it up (carefully) and check the plastic screws.  Like most Dells, I assume this one is made of cat food.   If one of the heat sink screws is cracked, then the heat sink will lift off of the CPU and you get hot dog temperatures.

Anyone up for a tailgate party?

---

### Post by whitesmith on 2014-10-17
> **trevor18 said:**
> Problem or concern i have is the cpu temp which sometime leads to the system bogging. Past few days ive ran it a few hours at a time and it hasnt overheat. But at idle the cpu temp is 60-70 degrees celcius.
At idle a CPU should never run that high. My machine typically runs 5% at idle with just a couple of browsers running. My core 0 temp is 47 Celsius. The problem sounds to me like a broken or incompetent heatsink. You really should look into this before your CPU melts.

---

### Post by trevor18 on 2014-10-18
I bought it new and have never dropped it, doesnt have cracked screw holes. I did remove the keyboard to upgrade the ram/hdd and ran windows 7 starter for months with no heat issues. This started when i formatted hdd and installed ubuntu. Right now im constantly monitoring the temp and shut down if it gets over 75.

---

### Post by tgalati4 on 2014-10-18
Have you check for speedstep settings in BIOS?  Make sure they are turned on.  Atom chipsets require throttling to stay cool.  Put a cpu frequency monitor on your panel and see if the CPU speed is going up and down.  If it stays at maximum all the time, then that will be a problem.

---

### Post by trevor18 on 2014-10-19
Well i deicided to remove ubuntu and i switched over to lubuntu 14.04 runs much smoother and the heat issue has changed dramatically. Just running firefox and browsing this forum it takes an hour for the temp to reach 65 degrees from a cold boot. But as it sits id have to take a break every hour or the temp will continue to rise so that hinders watching movies/games etc. on my machine. I installed the cpu freq monitor on my panel and it does seem to switch from 1000 to 1667 back and forth every few seconds. Other than heat it still runs everything perfectly.

---

### Post by tgalati4 on 2014-10-20
So it could be a design issue (the heat sink is too small) or improper heat paste application (quite probably).  Sometimes too much paste is put on the chip at the factory, which interferes with heat transfer.  The only solution is to take it apart and redo the heat paste correctly.

---

### Post by trevor18 on 2014-10-20
this computer ran hours at a time before i unstalled ubuntu with no issues. Im starting to think maybe its the thermal pads under they keyboard that transfer heat. They may have been removed when i replaced the hdd but im not certain, gonna pull it apart and see.

---

### Post by tgalati4 on 2014-10-21
That would do it.  Most small laptops require the case and other structures to dissipate heat.  Most manufacturers consider "lap-warming" a feature.

---

