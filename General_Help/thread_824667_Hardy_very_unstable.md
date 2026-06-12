---
title: "Hardy very unstable"
date: 2008-06-10
forum: General Help
---

### Post by K.Morgan on 2008-06-10
Something has happened recently that has made Hardy extremely unstable.  Every program that i use seems to just randomly close for no reason.

A couple of times today Hardy has just frozen completely, leaving the caps lock and scroll lock lights on my keyboard flashing, with the only way to restart the computer is to turn it off then on again.

Anybody have any ideas what's going on here?  I can't work in Hardy unless i can fix this as the programs i use will close before i get a chance to save the files.

---

### Post by housam on 2008-06-10
Do you have enough RAM / partition space for the system ? can you give us the specs of your machine .
Is Hardy your first ubuntu install ?

---

### Post by atryus28 on 2008-06-10
You're going to need to give more info other than it is randomly crashing.

Is this a laptop or desktop?  Are you using any network connection (hard to fathom nix without it but...)?  Are you using a wired or wireless connection.  If it is wireless what is your wireless adapter.

What have you done differently or changed (regardless of whether you think it important or not) recently?

What programs are you using that are locking up?

That's all I can think of for right now.

---

### Post by K.Morgan on 2008-06-10
I'm using a Desktop with a Pentium 4 2.0GHZ processor with 1GB of ram, everything has been running fine with no problems up to a week ago.  I haven't installed or changed anything new in the past week apart from Automatic Ubuntu updates.

Every program i use closes in the middle of using it, and it's different each time, sometimes it will close as i click on something other times it will just close if i move the mouse.  Programs i'm using are firefox, thunderbird, kompozer, Gimp, Inkscape, openoffice applications, all randomly close themselves.

Then now an again when those programs are not randomly closing the whole system will just freeze.

There's nothing i can pin point it to be, as i haven't done anything to my system apart from update Ubuntu.

---

### Post by bodhi.zazen on 2008-06-10
My guess is a hardware problem. These problems can be difficult to solve. One "guess" , is you CPU over heating ?

---

### Post by K.Morgan on 2008-06-10
Thanks bodhi.zazen Just checked my CPU activity and it is constantly jumping from 0% to 98% then back down again over and over.  Could this be causing problems, not sure if it means anything or maybe there's something running in the background causing it to keep spiking.

---

### Post by bingoUV on 2008-06-10
1. Any other operating system on the computer? Is it running fine?

2. Try running live CD for a while. Does it behave similarly?

3. Try memtest. Boot from the live CD and select the memtest option (I think the last option). Run it for at least 30 minutes. For such big troubles if due to memory problems, you will most likely get the error report in within 30 minutes, error would be in low memory area , less than 1 GB. If it is so, replace RAM modules and try again

---

### Post by atryus28 on 2008-06-10
When was the last time you bothered to clean out your machine?  A P4 is getting pretty "old" now and probably has amassed a large amount of dust.  Might even be a dust monster at this point.  My little sister's friend claimed her laptop was no good because it always overheated and shut down, and even claimed "it was always like that".  Then I took it apart and found, no exaggeration here,  3/4" of dust that I literally peeled off.

Put it back together and now it does not overheat nor do the fans run constantly.  Crack her open and vacuum out that dust.  Blowing it off just puts it back in the air.  If you use an upright over a shopvac turn off the beater bar and make sure you have no static charge built up.  I do this all the time, but the anal out there will tell you how terribly bad that is.  In 8 years of doing this I only zapped one stick of RAM and that was in a climate controlled storage room with a concrete floor.  Just touch something metal first if you are worried.  Computers are not as fragile as some might have you believe.

---

### Post by K.Morgan on 2008-06-10
Thanks for the advice guys, it appears that it may of been the processor.  I checked to see what temperature it was running at, and it was a very hot 96 degrees Celcius.

I took the PC apart and gave it a good clean and moved it to a different place to get maximum cool air circulation.  Managed to get the Temp down to 70 degrees which i think is still high but doesn't appear to be giving me anymore problems with Ubuntu, fingers crossed.

---

### Post by Titan8990 on 2008-06-10
Just a couple things to note:

Temps of 90C are hot enough to cause permanent physical damage to the CPU. 

Pentium 4s are hot CPUs to begin with and temps of 60-70 is normal. P4 when they reach a certain temperature are supposed to lower their clock speed in an attempt to prevent the CPU from becoming damaged. 

To sum it up I would no longer trust that CPU.

---

### Post by atryus28 on 2008-06-10
I would agree if it keeps having issues 90C is around the temp that it "could" be burnt out.  However, back in the day they were known to stop themselves from completely overheating even without a heat sink.  I would not be too worried unless nothing changes and it keep crashing.  I happen to have a pentium 4 cpu lying around from a client, though you may not have the right bios and memory for it.  It is a 2.4Ghz P4.  I am an AMD guy so I have no real use for it.

---

