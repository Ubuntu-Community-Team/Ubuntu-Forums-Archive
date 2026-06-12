---
title: "Have to delete &amp; re-install printer every restart"
date: 2008-01-14
forum: General Help
---

### Post by phidia on 2008-01-14
I posted this issue at linuxprinting.org a few days ago but since there have been no responses there I'm asking here. I also think that this might be a network problem-in that a powerbook running OS X can find and use the printer through wireless but the desktop that's connected physically to the router can't unless I set up the printer anew each time as described below.

I have a HP Photosmart 2575 all-in-one printer. Using ubuntu 7.10 & debian. I see this problem in both distros.
I can set up the printer and it prints fine but upon restart it won't print and I have to delete the previously created printer and go through set up all over again.

In /var/log/user.log I see this message (after the printer fails to print)

Jan 13 14:23:37 Photosmart_2570_series?ip=192.168.1.2: io/hpmud/jd.c 84: unable to read device-id

I did a search on that error but didn't find anything that looked useful. This printer is connected through the Ethernet port from the router. TIA

---

### Post by djrobthaman on 2008-01-14
I know this is a dumb question, but have you tried just turning off and then turning it back on again (the printer that is)?

I've never searched to see what my error is (so I don't know if it's the same one you're having), and it doesn't happen as frequently as yours, but every now and again I have the same problem where I just can't print anything.  But if I turn the printer off and then turn it on again it seems to always do the trick.

---

### Post by phidia on 2008-01-14
Thanks for the reply djrobthaman. I'm not at home right now but I'll try that. I would like a way to get it working correctly but if that works it's much better than going thru set up each time.

---

### Post by paperdiesel on 2008-01-14
I have the exact same issue, except that my printer is connected locally via USB.  It's a HP laserjet 3380.  If I go to system -> admin -> printers and add it, it will print beautifully.  But if I reboot and try to print something, it only prints half a page then hangs.

I can rinse and repeat these steps consistently.  What's up?  Why are my printer settings erased every time I reboot?

---

### Post by phidia on 2008-01-15
> **paperdiesel said:**
> I have the exact same issue, except that my printer is connected locally via USB.  It's a HP laserjet 3380.  If I go to system -> admin -> printers and add it, it will print beautifully.  But if I reboot and try to print something, it only prints half a page then hangs.

I can rinse and repeat these steps consistently.  What's up?  Why are my printer settings erased every time I reboot?

Are your settings actually deleted or is the the printer simply not responding correctly?
It really helps those troubleshooting to take a look at the messages in /var/log and post those that are relevant.

---

### Post by phidia on 2008-01-16
OK i had time to take another look at the problem which I created this thread about. It seems that after the update today (1-16-08) the printer now prints without the whole re-setup procedure. :)

---

### Post by phidia on 2008-01-21
I really like ubuntu so please try not to read or project anything into this.
This printer problem has returned again, and it's a real PIA! 

I get this message off & on > There was an error during the CUPS operation: 'server-error-service-unavailable'

In /var/log/messages there's this:

> Jan 21 13:07:01 Photosmart_2570_series?ip=192.168.1.3: INFO: open device failed; will retry in 30 seconds... 
Jan 21 13:07:34 Photosmart_2570_series?ip=192.168.1.3: INFO: open device failed; will retry in 30 seconds... 
Jan 21 13:08:40 last message repeated 2 times
Jan 21 13:09:46 last message repeated 2 times

I'm using a gutsy gibbon up-to-date. Is there anything I can do about this?

---

### Post by benny_boy on 2008-02-12
I'm having about the same problem, though i'm connected wirelessly on the laptop and the printer is a Photosmart 2600.  When i reinstall it after reboot, it works fine but if I don't, I get the same CUPS error some of the time and var/log/messages says this:

> 
Feb 12 19:21:10 bksk1lz Photosmart_2600_series?ip=192.168.1.104: INFO: open device failed; will retry in 30 seconds... 
Feb 12 19:21:44 bksk1lz Photosmart_2600_series?ip=192.168.1.104: INFO: open device failed; will retry in 30 seconds... 
Feb 12 19:22:50 bksk1lz last message repeated 2 times
Feb 12 19:23:56 bksk1lz last message repeated 2 times

Also, (i think i remember this correctly) there was one time where I printed after a reboot without having to reinstall. :confused:   And I have tried turning the printer off and on with no luck.

Any help?

---

