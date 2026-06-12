---
title: "Something has gone very wrong ..."
date: 2014-07-18
forum: General Help
---

### Post by Jay Car on 2014-07-18
[ATTACH=CONFIG]254822[/ATTACH]Scenario:
I use Ubuntu 13.04 on my desktop.  
I have a 3 year old, 7" Samsung Android tablet. 
I have several 32GB microSD cards that I add to the tablet, some are for photography trips, some are for general files like MP3s, etc. I swap them in and out, depending on what I need for the day.

I use a usb plug with a microSD convertor to plug the MicroSD into my desktop to move the photos or other files onto (or off of) the MicroSD card, which I then put back into the tablet. In all these years I've never had a problem with this method of moving and organizing the files on the MicroSD ... Until today.

Suddenly every Microsd card has become write protected.  I cannot move the files, delete them, or rename them.  My old standby for these situations (which haven't happened to me in years!) is gksudo nautilus ...

It doesn't work!  I've Googled and read till my eyes are crossed to find a way to change the write protection.  I thought maybe it was just one of the MicroSD cards had gone bad, but I've tried 3 of them so far and the write protection has gotten them all.  What in the world has happened?  What am I going to do with these useless MicroSD cards that won't even let me rename the photos?  This is crazy.  

I am soooo frustrated.  If anyone would like to try to help, I'd be very appreciative.

---

### Post by coldcritter64 on 2014-07-18
Hi Jay Car, I found [[COLOR=#0000cd]--this link--[/COLOR]]("http://askubuntu.com/questions/169976/micro-sd-card-with-adaptor-in-ubuntu-12-04-only-mount-read-only") that may be of some help. There are a couple of suggestions as to what can cause it ...  the one that seems most likely in your case with 3 cards not working is the second answer, it could possibly be dust in the reader slot.

Good luck, coldcritter64

---

### Post by Jay Car on 2014-07-18
I'm heading over to read the link right now.  :)

---

### Post by slooksterpsv on 2014-07-18
Its not like the microSD to SD converter card is it? If so, is the SD Card write protected? Some of them have the little white slider where you can lock the cards or not. Where you said USB I'm not sure if what I posted helps, but worth a shot right?

---

### Post by Jay Car on 2014-07-18
OK, I've read through the posts on the excellent link you gave me (thank you for that, it was one I hadn't seen).  I am sure the problem isn't dust, I just don't know why this started so suddenly. One of the posts on that link says this: "There is an option to Take Ownership in Nautilus" but I'm absolutely unable to get Nautilus to do any such thing ... apparently gksudo nautilus no longer works.  

I'll fuss with it a bit more tomorrow.  Maybe I just need to sleep ...  Thanks for helping.
  

file:///home/rch/Desktop/Screenshot%20from%202014-07-18%2019:25:12.png

---

### Post by Jay Car on 2014-07-18
> **slooksterpsv said:**
> Its not like the microSD to SD converter card is it? If so, is the SD Card write protected? Some of them have the little white slider where you can lock the cards or not. Where you said USB I'm not sure if what I posted helps, but worth a shot right?

I have an "All-in-one card reader/writer" with a built in usb cable.  I use a Sandisk MicroSD convertor that fits into the All-in-One card reader.  It's worked perfectly for years.  I even tried a brand new All-in-One reader with the same results.  I cannot express the sense of frustration I'm feeling.  I don't know what changed, I don't understand why it changed, and I don't understand why I can't figure out how to fix it.  

I'm feeling really tired and stupid right now.  :(

---

### Post by slooksterpsv on 2014-07-18
On the Sandisk Micro SD Convertor, on the left hand side there's a black slider (it's  in the notch), make sure that's slid to the top I believe. It could be white as well, see pic attached:
[ATTACH=CONFIG]254824[/ATTACH]

---

### Post by Jay Car on 2014-07-18
> **slooksterpsv said:**
> On the Sandisk Micro SD Convertor, on the left hand side there's a black slider (it's  in the notch), make sure that's slid to the top I believe. It could be white as well, see pic attached:
[ATTACH=CONFIG]254824[/ATTACH]

Hi slooksterpsv,
Yes, I checked it, it is at the top. I also got a new one, just to make sure it wasn't because the old one was failing.  Is it possible that the first one WAS failing and it corrupted the MicroSDs, so the new converter just read it as write protected?  I WAS able to copy all the files off of all the MicroSDs, tho I couldn't "cut" them or delete them off of the MicroSD, and I can't format the MicroSDs.  Maybe they are just lost and I need to toss them and get new ones?  

Sometimes I wish I'd spent more money on whiskey ... (just kidding)

:)

---

### Post by tgalati4 on 2014-07-18
If your power supply is failing, it is possible you are not getting a full 5VDC in your USB port and that is causing write errors and thus the file system is marked as "unclean" and thus not write-able.

Check voltages of your power supply in BIOS or with a voltmeter.  It is suspicious that all 3 cards would go at once.  Check your dmesg for write errors:

```
dmesg | more
```

spacebar to page forward, "q" to quit.

---

### Post by slooksterpsv on 2014-07-18
Hmm... it's possible that the locking mechanism is jammed and not functioning correctly. We can limit it down to a few possibilities:
1. It's Ubuntu, if you have another machine to test them in, if it works fine, then it's more than likely Ubuntu
2. The SD Card Reader/MicroSD Card Converter has a locking jam
3. USB controller issue.
4. Converter not compatible.

---

### Post by at_first_light on 2014-07-19
The first step is to isolate the problem to it's source, and then it'll be easier to solve the problem. There are 3 things in play here, the cards, the readers, and Ubuntu (the computer). I would suggest trying the cards under a live-cd, or on another computer. If the problem goes away you'll know it's a problem with Ubuntu (or the computer), but if the problem persists then you'll know it's either the cards or the readers.

[COLOR=#000000]If it turns out to be Ubuntu then reboot might be enough to fix it. I'm guessing it probably is a problem with Ubuntu (or the computer)[/COLOR][COLOR=#696969], but for the moment lets say that it isn't. The next step would be to determine if it's the cards or the readers. Since you've tried multiple readers it's not likely the readers. The laws of coincedence wouldn't possibly allow for all 3 cards to run out of writes (or die) at the same time so that just leaves something that the cards have in common aside from the reader. Have they been re-formatted since you used them on your computer last?[/COLOR]

---

### Post by Jay Car on 2014-07-19
> **slooksterpsv said:**
> Hmm... it's possible that the locking mechanism is jammed and not functioning correctly. We can limit it down to a few possibilities:
1. It's Ubuntu, if you have another machine to test them in, if it works fine, then it's more than likely Ubuntu
2. The SD Card Reader/MicroSD Card Converter has a locking jam
3. USB controller issue.
4. Converter not compatible.

OK, I'm awake, had some coffee, and I'm ready to tackle this again.  slooksterpsv, thanks for helping me to think things through. There HAS to be a simple explanation, and an easy fix (I hope).  So, let's do a process of elimination and see if we can figure out what ISN'T causing problems.  

I do have another machine to try these microSDs and converters on. It's a dual-boot Ubu-Pangolin/WinXP that has no Internet connection, so it hasn't changed in months and months.  I'll fire it up, and if the SD chips and converters still work on that machine then I'll know where the problem isn't.  :)

Back in a bit ...(to at_first_light, thank you for your excellent reply, I'm heading off now to try to pin-point the problem areas)

---

### Post by coffeecat on 2014-07-19
> **Jay Car said:**
> I do have another machine to try these microSDs and converters on. It's a dual-boot Ubu-Pangolin/WinXP that has no Internet connection, so it hasn't changed in months and months.  I'll fire it up, and if the SD chips and converters still work on that machine then I'll know where the problem isn't.  :)

Good idea. Try it in both operating systems. As someone said earlier, it's an unlikely coincidence that 3 cards should give the same problem simultaneously. If you can show that the cards work with another machine, then the problem is either with the hardware of your desktop machine or in your Ubuntu installation. Which leads me to a couple of comments in your first post:

> **Jay Car said:**
> 
I use Ubuntu 13.04 on my desktop.  


13.04 is long end of life. Whether or not the problem is with your 13.04 installation, you need to upgrade, preferably with a fresh installation of the current LTS 14.04. And if you are going to get the 14.04 ISO, then try booting up the 14.04 live session and testing your microSD cards in the live session. That way you may be able to tell whether the problem is with the computer hardware or with your 13.04 installation.

Also...

> **Jay Car said:**
> 
Suddenly every Microsd card has become write protected.

Did you get an error message when you tried to copy files onto the microSD card? What exactly did the error message say?

---

### Post by thenh813 on 2014-07-19
Just a few days ago I had a micro adapter die in a *VERY* unusual way, it would randomly go read only while writing big files. This constantly messed up the FS until the adapter finally wouldn't read. All they are is a few strips of metal going from the small pins to large ones, sometimes they get bent or worn out. Funny the adapter in question is a Sandisk also (usually really good brand). I had to format it to make it RW again, because of really bad FS corruption. Hopefully this isnt your problem, but I thought it was worth mentioning.

---

### Post by Jay Car on 2014-07-19
OK, I think this is solved:

After pondering the advice from everyone that posted here, I think I know what started the problem (and yes, it's a "PEBKAC/ID-10T error" story).  

This morning I fired up the old Pangolin/XP machine and plugged the "all-in-one" usb reader containing one of the microSD cards that were Read Only & Write Protected yesterday.  The MicroSD worked fine on Ubuntu Pangolin, I could cut, paste, rename, and organize all the files.  

Out of curiousity, I rebooted into XP and the card was still fine (copy, cut, paste and rename all worked). hmmmm.

So I brought the reader to this machine (Ubuntu 13.04) and plugged it in.  It worked fine. Tried the other two chips in the reader and they work fine too.  Tried the various chips in the other readers and they worked fine.

The only thing I eliminated from the mix was the adaptors. I had never noticed before that the all-in-one readers actually have a microSD slot, so the adaptor wasn't needed. 

So, what started the problem yesterday? Here's my guess ...

The first MicroSD came out of my Samsung Android tablet. When that tablet is turned off, the screen turns a dark grey, but after a few more seconds it goes completely dark and is truly shut off. I was in a hurry yesterday and may have taken the chip out too soon. 

I then popped it into the adaptor (that was inserted into the all-in-one reader), and plugged the whole thing into the Ubu-13.04 computer which read the chip as being write protected & read-only, and refused to let me make changes to any of the files - which could have been caused by me impatiently pulling the card from the tablet before it had properly shut down, maybe?  

I then grabbed another microSD chip, popped it into the same adaptor and reader, and the computer read THAT one as write protected and read-only too.  Which caused me to start pulling out the other readers and adaptors and trying them all, getting the same results.  

At that point, IF I'D SIMPLY RESTARTED THE COMPUTER I THINK THE PROBLEM MIGHT HAVE BEEN RESOLVED RIGHT THERE. 

Or, if I had just put the first chip back into the tablet and restarted it and then shut it down properly before removing it, the problem likely would have been solved right there.

I believe that once Ubuntu read the first chip as read-only, it saw all the others the same way until I restarted the computer this morning.  Now all the chips are readable and useful again.

So, if anyone else has the same problem, here are some things to try:

1. Be patient and think it through before doing a million different things that only confuse the issue.
2. Don't get mad and break open the poor adaptors and break their little switches off (see pics).
3. Try simple solutions first (restart the computer for example, I forget to try that since I stopped using Windows, but even with Ubuntu it can occasionally help)
4. Always make sure to safely remove microSD chips, usb drives and readers, etc. 

5. And most importantly, always remember to thank the patient helpers on the Ubuntu forums ... I know for a fact that without them I'd be LOTS stupider than I already am. (it's ok to laugh, I can take it :)

To coldcritter64, slooksterpsv, tgalati4, at_first_light, and the ever awesome coffeecat, thank you for all your help. If you've read this far, you all deserve medals and applause. 

Coffeecat, I promise to install something better than 14.04, soon.  :)

[ATTACH=CONFIG]254835[/ATTACH][ATTACH=CONFIG]254834[/ATTACH]

---

