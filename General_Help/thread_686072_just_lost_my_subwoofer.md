---
title: "just lost my subwoofer"
date: 2008-02-02
forum: General Help
---

### Post by malfist on 2008-02-02
I was listening to my music on my logitech system and all of a sudden my subwoofer quites playing. I can't get it working again. It's the hub of the system so everything goes through it but every other speaker works (side note, the other 'center' speaker which is on the same cord to the sound card doesn't work and hasn't worked since soundcard upgrade).

ALSA's been giving me hell lately and I think it might be related to that. Or I could have blown it. I've listened to my music quite a bit louder that it was. It was about 3/4 on the main dial and subwoofer was around 1/2 and Alsamixer was set to 80%.

Tested in windows and only rear speakers worked but it was Vista and Vista could quiet possible have more bugs than ME.

Any ideas?

---

### Post by nemilar on 2008-02-02
If it just stopped working suddenly like that, and it doesn't work in Vista, my bet would be on a hardware problem.

:( sorry

---

### Post by Shazaam on 2008-02-02
Got cats? I had a cat that loved chewing wires.
Aside from that, check all of your connections. Unplug them and plug them back in. It could also be a bad sound card since Windows has problems too.

---

### Post by Rocket2DMn on 2008-02-02
I would check all the wiring, then unplug the power from the speaker system (probably on the back of the sub).  Count slowly to 10 and plug it back in with the power in the off position.  Then turn the system on with the dial at a relatively low volume.
You can try plugging it into something like an ipod too and see what happens.

---

### Post by malfist on 2008-02-02
This is the system: [http://www.logitech.com/index.cfm/speakers_audio/home_pc_speakers/devices/234&cl=us,en](http://www.logitech.com/index.cfm/speakers_audio/home_pc_speakers/devices/234&cl=us,en)

I unplugged the stuff, but I will try again. Sound card is brand new, not more than a month old. The issues with vista may be it was using default drivers for the first time with no reboot after reinstalling.

No cats :P, in a dorm.

---

### Post by Rocket2DMn on 2008-02-02
> **malfist said:**
> This is the system: [http://www.logitech.com/index.cfm/speakers_audio/home_pc_speakers/devices/234&cl=us,en](http://www.logitech.com/index.cfm/speakers_audio/home_pc_speakers/devices/234&cl=us,en)

I unplugged the stuff, but I will try again. Sound card is brand new, not more than a month old. The issues with vista may be it was using default drivers for the first time with no reboot after reinstalling.

No cats :P, in a dorm.

Ahh, dorm life.  Been there - make sure you blast everybody else away!  Looks like a great system :)
Try plugging the speakers into another system, if they don't work there, then it is almost certainly a hardware problem.  Resetting the power should work, otherwise you probably blew something out, or perhaps the system is just defective - is it new?  Check your warranty on it.

---

### Post by malfist on 2008-02-02
The speaker system is a little over a year old (no more warrenty). I powered off and rebooted. Unplugged everything. Still the same issue.

Is there a way to redo my entire ALSA? sudo aptitude purge alsa-base alsa-utils doesn't seem to do it. At least not fully.

Alsa was working perfectly, then I got a sound baster audigy SE and screwed it up trying to get it working but it never did so I bought a new card and alsa works but acts funny.

My laptop may be able to handle the speakers. All the speakers work except the sub (to which everything is connected to and from), even the center speaker works when 'matrix' is enabled.

---

### Post by malfist on 2008-02-02
worked in lappy after a few tries. Then when I plugged back into desktop it worked for like 2 seconds before going out. Check soundcard/motherboard connect?

---

### Post by Rocket2DMn on 2008-02-02
If it only sometimes works on the laptop, I'd say cable problems perhaps, but if it works all the time on the laptop, then you probably have a problem with the sound card (since it doesn't work with vista either).

---

### Post by malfist on 2008-02-02
did not work in lappy first two times, after third plug in worked without going out for several minutes. Lost it when plugged back into desktop. I reconnected the soundcard in the desktop and it's still not working.

Cables come straight out of the sub so I would have to cut and soder to replace them, not fun.

What about alsa?

---

### Post by malfist on 2008-02-02
I think I will test with a liveCD.

---

### Post by Rocket2DMn on 2008-02-02
I would say troubleshoot it with vista first, call tech support for whoever you need to.  If they can help you fix the problem, then we know it's software.
If it can't be troubleshooted in windows, then we can be pretty sure it's an audio card failure.

---

### Post by malfist on 2008-02-02
Does not work in DSL's toram live cd :( Then again, a lot of the sound card doesn't work either, only the front two speakers work.

---

### Post by malfist on 2008-02-02
Did not work with ubuntu's live cd, assuming the fault lies with cable or sound card.

---

### Post by malfist on 2008-02-02
can't get it to work in lappy now. :(

---

### Post by Rocket2DMn on 2008-02-02
Well, I'm not really sure what to tell you.  It just sounds so irregular, it could be messed up speaker system.  You may have to call logitech and see what they say (do it through vista so they can actually help you).

---

### Post by malfist on 2008-02-02
Switched cabling (only power is internal, and cable *from* the satelites) and problem persisted on laptop. I will call logitec at a later date. For now, assuming something has happened to the subwoofer. I'm going to take it appart and look at and see if anything looks broken inside it.

---

### Post by malfist on 2008-02-03
Grrr, can't take it apart, outside box is just glued together :(

---

### Post by malfist on 2008-02-03
followed logitechs instructions from here: [http://logitech-en-amr.custhelp.com/cgi-bin/logitech_en_amr.cfg/php/enduser/std_adp.php?p_faqid=2913&p_created=1125714076&p_sid=LjP-dmXi&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9OTAsOTAmcF9wcm9kcz04NDQsMTcmcF9jYXRzPSZwX3B2PTIuMTcmcF9jdj0mcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9ubCZwX3BhZ2U9MQ**&p_li=&p_topview=1](http://logitech-en-amr.custhelp.com/cgi-bin/logitech_en_amr.cfg/php/enduser/std_adp.php?p_faqid=2913&p_created=1125714076&p_sid=LjP-dmXi&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9OTAsOTAmcF9wcm9kcz04NDQsMTcmcF9jYXRzPSZwX3B2PTIuMTcmcF9jdj0mcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9ubCZwX3BhZ2U9MQ**&p_li=&p_topview=1)

According to that, it's my sub. Tested with mp3 player as source. Swapping cabling didn't do anything.

 Music sounds awful without the sub :*(

---

### Post by malfist on 2008-02-03
warrenty is two years, maybe I can get a replacement or refund. But I don't have a reciept :(

---

### Post by Rocket2DMn on 2008-02-03
> **malfist said:**
> warrenty is two years, maybe I can get a replacement or refund. But I don't have a reciept :(

Call them, you shouldn't have to have a receipt.  If they tell you no, tell them to escalate your problem to somebody who can help since you legitimately own the system.  Don't take no for an answer, be firm (but not rude).

---

### Post by malfist on 2008-02-03
Yeah, I did that with Gateway and I spent two months on the case and never got the 'update' the 'offered' for my laptop. They even lied on their comments to the BBB!

I'll see where I get, not all companies are like Gateway (Newegg rocks!). I sent them an e-mail, I will call tomorrow if I have free time, which means probably not. I don't really have time to do this either :( Damn honor's classes and damn Japanese classes and damn new jobs that don't ask how many hours you want to work and instead give you the max the campus will allow students to work. /rant.

---

### Post by malfist on 2008-02-03
Called logitech, they're going to replace it. I just have to cut off the wired remote and ship it in and they will send me a new system or sub, I don't remember which.

---

### Post by Rocket2DMn on 2008-02-03
> **malfist said:**
> Called logitech, they're going to replace it. I just have to cut off the wired remote and ship it in and they will send me a new system or sub, I don't remember which.

awesome, post back if you still have problems.

---

