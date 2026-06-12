---
title: "Video games freeze computer"
date: 2013-09-07
forum: General Help
---

### Post by Crayboff on 2013-09-07
Whenever I play video games that involve 3D graphics (DOTA 2 and Minecraft are the only two I've tested), my computer will freeze after a seemingly random amount of time. Sometimes my computer freezes for 10-15 seconds and seems to fix itself, but then inevitably it will freeze and I'll be forced to shut down my computer by holding down the power button. Now I sometimes get graphics glitches on websites where some buttons may be blurred and then reset if I hover over it or scroll the page down and back up.

I'm running Ubuntu 12.04.

Here is my graphics card info:
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

This all first started when I installed DOTA 2 (via Steam) and was having problems with trees and heroes being invisible. I [found this post and followed the instructions](https://github.com/ValveSoftware/Dota-2/issues/264#issuecomment-21307561):

> 
Ok, finally it's solved. Hope this help another players trying to get it working in Ubuntu 12.04 using Intel Graphics

apt-add-repository ppa:qos/mesa didn't work in precise, apt-get update shows packages not found for precise from qos/mesa in output

Instead I used

sudo add-apt-repository ppa:xorg-edgers/ppa 
sudo apt-get update
sudo apt-get upgrade

At the begining it showed that there was nothing needing to be upgraded so I look into my software sources and noticed ppa:xorg-edgers were unchecked, so I checked them and then again

sudo apt-get update
sudo apt-get upgrade

This upgraded a few packages but not my mesa version, so I used

sudo apt-get dist-upgrade

and then mesa was upgrated from 9.0 to 9.1.5 (the one I first tried to install from source at the begining -.-)

after that I rebooted just for fun and then I tried to run Steam, but got an error saying Gen6+ requires Kernel 3.6 or later so Steam never started and to solve that I upgraded my kernel to 3.8 using

sudo apt-get install linux-generic-lts-raring

Then I was able to start Steam again, so I ran Dota, started a practice with bots and finally I was able to see all the heroes and the forest :) At the end it was in fact a mesa problem caused by old mesa version

Sadly I'm still getting really low performane, specially in the lobby which I didn't mention before because I saw it was already posted in another Issue (don't remember the number of the issue right now) so I will just follow it to see how it goes.

Sorry for my bad english it's not my native language and I really tired at the moment because of some personal issues...


After I followed the above instructions, DOTA started working, however now I'm starting to crash. How can I undo the above, I'd rather not be able to play dota than crash all the time (but if there's some way to get everything to work, that'd be best)?

If there's any more info I need to provide, let me know how to get it for you.

---

### Post by bewareofthephog on 2013-09-08
I have no idea what it could be, but just a shot in the dark have you checked your cpu and video card temps with lm-sensors.  I had a bunch of odd system crashes and freezing.  I just happened to be in my BIOS for another reason and saw my CPU was running 740C!!  I bought a new heatsink and my temps dropped to sub 30 and haven't had a problem after that.  I doubt it's the same issue but it's worth checking.

---

### Post by Crayboff on 2013-09-08
> **bewareofthephog said:**
> I have no idea what it could be, but just a shot in the dark have you checked your cpu and video card temps with lm-sensors.  I had a bunch of odd system crashes and freezing.  I just happened to be in my BIOS for another reason and saw my CPU was running 740C!!  I bought a new heatsink and my temps dropped to sub 30 and haven't had a problem after that.  I doubt it's the same issue but it's worth checking.

You might be on to something, despite having my computer in a well ventilated area, it would still crash. I checked the core temps with lm-sensors. Not playing the video game kept me around 55-60°C and when I was playing I was between 70-80°C, the sensors also have this next to each report: (high = +80.0°C, crit = +85.0°C) so perhaps it's getting over 85°C. I can't test it when it's actually freezing.

When it does freeze the fans first stop and then pick up blowing out hotter and hotter air until I force shut down the computer. What I don't understand is why this started happening after I did the software stuff I noted in the OP and not before. I used compressed air to blow out the little dust that was in there (it's a laptop so I can't just add a new heatsink), and it doesn't seem to help too much.

---

### Post by CatKiller on 2013-09-08
> **Crayboff said:**
> What I don't understand is why this started happening after I did the software stuff I noted in the OP and not before.

If the software is enabling your hardware to work harder, it will produce more heat. That extra heat might be the difference between staying within tolerance and not.

Or it could be a memory problem, or a problem with the driver (it's called Edgers for a reason). Or something else.

My first instinct on reading your post was to think of temps too, though.

---

### Post by Crayboff on 2013-09-08
> **CatKiller said:**
> If the software is enabling your hardware to work harder, it will produce more heat. That extra heat might be the difference between staying within tolerance and not.

Or it could be a memory problem, or a problem with the driver (it's called Edgers for a reason). Or something else.

My first instinct on reading your post was to think of temps too, though.

Any suggestions of what I can do to prevent this from happening again? How can I change the software to something that works better?

---

### Post by CatKiller on 2013-09-08
You could set up something that periodically logs the temperature so that you can check on the next boot if the computer was hot when it crashed. If it turns out to be temps you can get more aggressive with cooling or under-clocking.

If it's driver instability you can switch to something less performant but more stable.

You can run memtest and fsck to check your memory systems for problems. A hard drive test is often a good precaution too.

---

### Post by bewareofthephog on 2013-09-08
> **Crayboff said:**
> You might be on to something, despite having my computer in a well ventilated area, it would still crash. I checked the core temps with lm-sensors. Not playing the video game kept me around 55-60°C and when I was playing I was between 70-80°C, the sensors also have this next to each report: (high = +80.0°C, crit = +85.0°C) so perhaps it's getting over 85°C. I can't test it when it's actually freezing.

When it does freeze the fans first stop and then pick up blowing out hotter and hotter air until I force shut down the computer. What I don't understand is why this started happening after I did the software stuff I noted in the OP and not before. I used compressed air to blow out the little dust that was in there (it's a laptop so I can't just add a new heatsink), and it doesn't seem to help too much.

How long has it been since you've put new paste on your cpu?  I didn't need to replace the heatsink and fan it was just an upgrade I had been meaning to make.  When I had taken the stock one off I noticed all the paste had been burned off.  You might want to check that.  It's the one thing on a computer I hate doing because depending on your mobo it can be a pain to remove the heatsink.

---

### Post by Crayboff on 2013-09-08
> **bewareofthephog said:**
> How long has it been since you've put new paste on your cpu?  I didn't need to replace the heatsink and fan it was just an upgrade I had been meaning to make.  When I had taken the stock one off I noticed all the paste had been burned off.  You might want to check that.  It's the one thing on a computer I hate doing because depending on your mobo it can be a pain to remove the heatsink.

It's a laptop, I'm not really comfortable enough with hardware to take it apart and mess with things :(

---

