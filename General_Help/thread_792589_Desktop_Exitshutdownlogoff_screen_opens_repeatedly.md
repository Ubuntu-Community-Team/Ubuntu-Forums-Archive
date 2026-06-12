---
title: "Desktop: Exit/shutdown/logoff screen opens repeatedly. Computer shuts down suddenly."
date: 2008-05-13
forum: General Help
---

### Post by 2percentright on 2008-05-13
A couple weeks ago a strange occurrence started on my Ubuntu 7.10 install.

I'd be working and the Logoff/shutdown/restart/etc window would open as though I had clicked the powerdown button.  I would then spend a handful of minutes clicking "cancel" to close the window, only to have it reappear a minute or immediately.  Eventually, the window would close and stay closed for a length of time.  I was worried, but it only last for a day or two.  That was about a month or two ago.

Now it's back, and worse than before.  Not only will it open the logout/shutdown/restart window over and over again, my entire system will just shutdown completely without a warning or noise or anything, as though I pulled the plug.  Pushing the power button on the tower restarts the whole system without a pause.  A couple times, I've had the system shutdown completely, then proceed to restart on its own.

I've read some threads about sudden shutdowns; that they are often attributable to overheating. My fans are running and I've never had a heating problem in the past. Also, those threads often talk about the system simply shutting down while the system is stressed or etc but never showing a screen or window, like with my case.

I get the paranoid feeling that the computer is somehow executing a "open shutdown window" command sometimes followed by "execute shutdown" and/or "execute restart." which makes me think it is a software problem rather than a hardware problem like overheating or faulty power supply.

Anyone experienced anything similar to my problem?
Anyone have any idea what to look at to gain more information? Is there a logfile somewhere that lists all the commands executed on the session that I could find what the system was doing right before it shuts down or opens a logout window?

Anyone have anything?

(Desktop system running 7.10 kernal 2.6.22-14-generic Gnome 2.20.1
RAM: 1.5 GB
Processor: AMD Athlon XP 3200+)

---

### Post by zenwalker on 2008-05-13
Hope u r not using ur system at root user and not install alll the packages avail out there...

---

### Post by 2percentright on 2008-05-13
> **zenwalker said:**
> Hope u r not using ur system at root user and not install alll the packages avail out there...

You think I may have installed a malicious program of some kind?  I don't recall installing anything questionable recently.  Anyway to find out?

---

### Post by bwphilip on 2008-05-13
If you do have a power button on your keyboard, perhaps your keyboard is malfunctioning and "sending" the power button when you aren't pressing it.  My old keyboard I had to retire because it "typed" wrong letters when I hit different keys.  If you have a power button on your keyboard, you might try a different keyboard.  Cheap keyboards are available at target or your local big box store. When I got a new keyboard, I kept hitting the power button mistakenly and this would happen, but I can imagine it being a problem like my old keyboard had too.

---

### Post by chrisccoulson on 2008-05-13
It definately sound like a power button event is happening. This is the behaviour you'd expect from continuosly depressing the power button. Try changing the reponse to the power button in the power settings to 'Do Nothing' to see if it goes away. (I think it is possible to do that anyway, I can't check at the moment)

---

