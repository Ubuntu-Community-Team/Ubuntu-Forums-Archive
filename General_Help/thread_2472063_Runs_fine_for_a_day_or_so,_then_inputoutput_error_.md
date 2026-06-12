---
title: "Runs fine for a day or so, then input/output error for everything"
date: 2022-02-16
forum: General Help
---

### Post by goemonburo on 2022-02-16
I'm baffled by this:  Have had a perfectly working system for several years, then just within the past week, have had repeated system failures.  It's running Lubuntu 20.04LTS.  

It works fine for a day or so, then nothing works.  If a terminal is already open, I can type "df" and see that the disks are not full, but if I type "firefox" or "top" or anything else, it says "input/output error."  I cannot use the GUI either...if I click a button, it just hangs, with nothing happening.  

I can't shutdown the system, either...no commands work.  All I can do is a hard shutdown.  And when it boots up it works fine again for hours or a day or so...then the same thing happens.

I feel like something must be filling up or some event is triggering the failure, as it works fine initially.  

Would love some suggestions as to what I'm doing...or doing wrong.

---

### Post by Autodave on 2022-02-16
Could be software or hardware issue.  I will try to help on the hardware side and let the way more knowledgeable people here have a go at the software side.  If this is a laptop, have you tried blowing the dust out of it?  Could be overheating.

If desktop, try removing the side cover and run like that......it will allow more cool air into it.  Are fans all spinning and clean?  How about CPU cooler....clean?  If you are using any USB hubs, *especially* powered hubs, disconnect them and try.  Run a RAM test.  Try another good keyboard and mouse.  When it locks up, turn mouse over and look to see if laser is lit brightly or not at all.

---

### Post by erind on 2022-02-16
It looks like a hardware (hard disk) error. Just run a disk check (GUI or command line) and see what it says. Maybe it's time to backup everything and replace the disk.

---

### Post by Autodave on 2022-02-16
If you even suspect a HD failure, the very first thing that you do is copy EVERYTHING that you need off of the drive before you do *anything *else!!!

---

