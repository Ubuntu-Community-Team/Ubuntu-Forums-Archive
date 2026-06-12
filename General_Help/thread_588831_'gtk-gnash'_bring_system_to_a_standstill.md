---
title: "'gtk-gnash' bring system to a standstill"
date: 2007-10-23
forum: General Help
---

### Post by Sporkman on 2007-10-23
When my wife browses various multiple sites, sometimes the system gets bogged down to an unusable state. When, after several minutes I'm able to to look at the system processes, I see several "gtk-gnash" processes hogging the CPU. How can I avoid this?

---

### Post by Acglaphotis on 2007-10-23
Installing Adobes flash plugin?

---

### Post by mrtbone on 2007-11-05
had the same problem. installing adobe plugin helps

---

### Post by Hajo Harts on 2007-11-20
If you have a AMD-processor, like I have, and installed the Ubuntu 64 bit version, like I did, then you can't install Flash, because it is not available for the 64 bit AMD processor.

---

### Post by K.Mandla on 2007-11-20
Moved to General Help.

---

### Post by nhiemnb on 2008-01-25
hi Sporkman!

FireFox added more a plugin Gnash SWF player (gkt-gnash)when it run  make up 80% over CPU process. Hence, have to remove Gnash SWF Player package by commanding: 
sudo apt-get remove --purge gnash gnash-common mozilla-plugin-gnash

---

### Post by wrgarrett on 2008-02-22
> **nhiemnb said:**
> hi Sporkman!

FireFox added more a plugin Gnash SWF player (gkt-gnash)when it run  make up 80% over CPU process. Hence, have to remove Gnash SWF Player package by commanding: 
sudo apt-get remove --purge gnash gnash-common mozilla-plugin-gnash

Thank you so much for this info! Works great! Someone should post a gtk-gnash warning or remove the package. This behaviour is unacceptable. I hope others benefit from your solution!

---

### Post by dotdot on 2008-03-25
i had the same problem - this kind of rubbish is what gives the whole os a bad name.

how do you reckon your average punter is going to fix this eh ?:mad:

windows - yes sad - i know - almost as sad as the solution.

..

let's hope this is not in the repos for LTS.

---

### Post by callahanp on 2008-05-17
I was getting the same thing.  In my case had just upgraded my PC to an E8400 Core Duo.  It was not as fast as I expected.  In fact it was no faster than the Pentium III 650 it replaced.

**The Problem:**
[LIST]
[*]A brand new box with a Gigabyte GA-P35-S3G motherboard, Core 2 Duo E8400 cpu, 4G memory was not performing as well as I had expected.
[*]After each reboot, and within a few minutes to over an hour: the mouse started to slow down its response.
[*]It would respond to mouse movement but would jump slowly and sluggishly across the screen. 
[*]I could not open a new application.  
[*]The disk drive light was on solidly Then the system froze up completely. [/LIST]

This occurred from several minutes to several hours but on nearly every boot.

**Partial Solution:**

[LIST]
[*]I rebooted and opened gkrellm, a couple of terminal windows and firefox.  
[*]I ran top in one of the terminals.  
[*]gtk-gnash was right at the top, taking aproximately 50% of cpu.  This led me to this thread.  Lucky me!
[/LIST]

Commands:

[FONT="Courier New"]#ps -aux|grep gnash[/FONT] 
This command showed 4 processes (only one was taking the 50%
[FONT="Courier New"]
#killall gtk-gnash [/FONT]
stopped them all 

[FONT="Courier New"]#sudo apt-get remove --purge gnash gnash-common mozilla-plugin-gnash [/FONT]

This got rid of gtk-gnash permanently.

[B]Summary:
[/B]
[LIST]
[*]I had a box that was slower than it should have been and it kept slowing and freezing.
[*]Testing showed that gtk-gnash was running and using 50% of 2 cpus.
[*]Killing the gtk-gnash processes reduced the load on the cpus from 50% each to 1-2% (mostly idle and typing)
[*] After several more hours the system froze again, with the same mouse behaviour.  

[/LIST]
I'll worry about a replacement swf player later.

I'll revise this post as I figure this out.  This could still be a remnant of gnash, as I did not reboot after the cleanup, but It doesn't look good.  


**Credits:**
A big thank you to nhiemnb for the command to remove gnash entierly!

[INDENT][INDENT][INDENT][/INDENT][/INDENT]-30-

---

### Post by Prometheum on 2008-07-01
While I don't have this problem, a friend of mine does, and a good way to reduce it is to install the NoScript plugin, available in the repos. NoScript blocks all clientside executable content in Firefox, making your browsing faster and more secure. If you absolutely need to enable a site that relies on/abuses java/javascript/flash, you can add a permanent or temporary exception.

This will block the flash content from loading in the places you don't want it to load on. Installing the Adblock plugin also helps, since I've found a lot of the load is gnash needing to constantly render banner adds that use flash.

---

