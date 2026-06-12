---
title: "Laptop can't recover from Hibernate"
date: 2007-05-23
forum: General Help
---

### Post by newatthis88 on 2007-05-23
So...I just installed Feisty on my laptop a week ago and was pretty darn impressed with it.  Everything was working fine until I tried to make the laptop go to standby/hibernate.  It eventually went to "sleep" with the one light at the front blinking to indicate that it was hibernating.  However, when I tried to wake it up, the fan would blow, the cd drive would hum and the power light would turn on, but the screen would be blank.  Actually, it seems that the screen is not even getting power and neither is my optical mouse as it is not lighting up.  

I then turned the laptop off by holding the power key and then restarting and it's the same thing: fan humming, cd-drive responding, but no power to the screen or to the mouse.  I tried plugging an external monitor in but it's not getting a signal.  

I could tell you the general specs of my computer, but as for the driver details, I can't even USE the computer at the moment so there's no way I could look them up.  

I would really appreciate any comments/advice/suggestions that are out there.

---

### Post by aroch1 on 2007-05-23
One of the sore issues with linux on laptops has been poor support for hibernation.  I had this problem the first (and last) time I tried to get my laptop to hibernate, and rebooting a couple of times (it took 3 or 4) worked for me.

---

### Post by wastedfluid on 2007-05-23
I think the support for hibernations is just not great enough.  I, too have problems with hibernation.  I get vertical orange+black lines.  I just shut the laptop down and wait the twenty seconds it takes to re-boot.

---

### Post by loathsome on 2007-05-23
> **wastedfluid said:**
> I think the support for hibernations is just not great enough.  I, too have problems with hibernation.  I get vertical orange+black lines.  I just shut the laptop down and wait the twenty seconds it takes to re-boot.

Same here. Can't get it to either suspend or hibernate. I just shut it off.

---

### Post by newatthis88 on 2007-05-23
Well....I guess I'll try rebooting a few more times.  I've done it about 4 times now and the laptop is still not responding.  Any other suggestions?  Is there a way that I can force the computer to get out of standby?

Thanks for the replies so far.

---

### Post by oliverb4ss on 2007-05-23
I have the same problem as the original poster, but in my case after I manually shut it down (power button), it starts up normally.

But yeah, after trying to recover it from stand by, the fan and cd hum, but nothing on the screen.

Help is much needed!

---

### Post by newatthis88 on 2007-05-23
Ok, so I have a fix for my particular problem, courtesy of instructions from a friend who used to do tech support.  

Since my laptop wasn't restoring even after a reboot, I had to disconnect the AC adapter, remove the battery and then hold down the power button for 10-15 seconds.  Then re-insert the battery, plug the adapter in and power up the computer.  

This got my laptop booting  again, thankfully.  Now that I know better, will NEVER try to hibernate it ever again.

---

### Post by angryfirelord on 2007-05-23
I believe it's some ACPI issue that the kernel still has issues with. You can tell it does wake up, but it doesn't activate the screen or anything else. Sleep would be useful so I don't have to constantly shut down my machine, but Ubuntu loads fast enough for mostly everyone anyway.

---

### Post by loathsome on 2007-05-24
Sometimes the laptop I have (Sony VAIO) *does* actually "hibernate". It looks like everything's ok, but when I start it again, it's a completely new session - just like I had turned it off.

I sure hope the ACPI-support for this is much more improved in the next kernel version :)

---

