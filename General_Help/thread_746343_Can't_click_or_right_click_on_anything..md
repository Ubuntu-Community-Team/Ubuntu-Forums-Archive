---
title: "Can't click or right click on anything."
date: 2008-04-05
forum: General Help
---

### Post by Roasted on 2008-04-05
So I just got on my gutsy machine and nothing seems to respond. I've rebooted twice, logged off 3 times, and given it ample time to boot up and it still is giving me trouble. When I hover the mouse over the icons and whatnot, they animate as if they are clickable, but clicking does nothing. When I hit F8 to open my home directory, I cannot click on the X to close it. I must altf4 it.

What the hell happened?

---

### Post by Roasted on 2008-04-05
Next time I think I need to troubleshoot more closely. By unplugging my new usb mouse I got last night and plugging it back in, it fixed it. I don't know what in the world happened to it, though, so if anybody can explain it I'd love to hear! 

Leaving this up so some people may be able to learn from my mistake!

---

### Post by Roasted on 2008-04-05
So it just happened to me again. I had to unplug my mouse and plug it back in in order for it to work properly again. What in the world causes this? My old PS2 mouse never had this issue. This mouse is brand new... bought it last night.

Edit - oh wow, I just figured something out. My phone sits on my desk next to my speakers and near my mouse. Every so often, my phone (ATT, GSM) will do a scan I guess to re-acquire signal to towers. This basement is a killer to cell phones. When it does, it locks up my mouse. I can move it, I just can't click. If I unplug it and plug it back in, it works fine. Weird...

---

### Post by alterpinguin on 2008-04-15
> **Roasted said:**
> So it just happened to me again. I had to unplug my mouse and plug it back in in order for it to work properly again. What in the world causes this? My old PS2 mouse never had this issue. This mouse is brand new... bought it last night.

Edit - oh wow, I just figured something out. My phone sits on my desk next to my speakers and near my mouse. Every so often, my phone (ATT, GSM) will do a scan I guess to re-acquire signal to towers. This basement is a killer to cell phones. When it does, it locks up my mouse. I can move it, I just can't click. If I unplug it and plug it back in, it works fine. Weird...

have similiar problem and i doubt its based on hardware(maybe with software timeing)
- i used a ps2-only-mouse over 2 years with no problems (different linux-distributions)
- bought a new usb-mouse with little ps2-dongle (means it could plugged in ps2 or usb)
-
then it happened after a week, suddenly the mouse stopped during work - no move, no click
and it happend with the ubunt 7.04 version i had no mouse-problems with the old mouse since nearly a year (spring last year).
it was plugged in the ps2-mouse-port and i did not want to unplugg it (those ports are NOT made for hot-plugging, instead of the usb-ports and one might damage the mainboard), but i did a software reset and the mouse did not work, then i did unplugg it and it did response at once in the running x-server-session. 
It happened again some days later (around a week) - and i decided to try it in the usb port.
around a week later, the mouse did stop working in the usb-port too, but after quick unplugg it continued to work again - needless to say, i checked the log-files for any messages, but there was nothing about usb-device errors

i could have used my old ps2-mouse again, but because i could not reproduce this fault, i am still trying on - and now it did not happen since over 2 weeks during a session, but one time the mouse did not work on coldboot( computer-start in the morning..)

But i am shure it happens not randomly and my mate has a computer with an expensive razor-mouse and there happens the funny thing: the mouse works in linux but when he reboots out of linux (warmboot) into windows for some gaming the razor-mouse does not work any more and needs to be re-plugged to work (its an usb-mouse too)
should i say its windows faults to not recognize the mouse? even with the propriatary razor-mouse-drivers installed? - 

my thoughts: its not a only software problem, so you should try to get hand on different other usb-mouse hardware (different manufactorer) to test and if possible test your mouse at other computers - it might be only a problem of the combination - mainboard+usb-chipset and this mouse.

---

