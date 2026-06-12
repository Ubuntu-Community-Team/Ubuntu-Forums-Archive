---
title: "[SOLVED] Fresh Feisty Install - CPU temp @ 62!  Help."
date: 2007-09-27
forum: General Help
---

### Post by drsmaw on 2007-09-27
I have read other forums on this and still havenot found an answer. I am running and Intel P4 3.2ghz (64ht), Mobo: Intel 945GCCR, 160gb hdd , intel graphics.
Fan is always on, according to BIOS my CPU temp is 62, internal temp is 45, and remote temp is 45.
Tried lm-sensors, sensors-applet, powernowd ( no luck). Tried to turn off hyperthreading ( no luck).
tried sensors-detect and got this = I2c adapter drivers (i2c-1801), Chip Drivers ( eeprom). Either way, none of this has helped me control my fan or CPU temp.
I am looking for any suggestions, thank you.

This was a problem o had last year with 6.06, then deleted everything and figured i would wait for Feisty, but I have the same problem.
Should I be using the 64bit version?

---

### Post by SeanTater on 2007-09-27
I'm having difficulty understanding your problem, but if you mean that you CPU temp is too high, you might consider putting new thermal paste on your CPU. It only costs about $5 to $15 on average and can cool your CPU temp considerably.. It takes about 10 minutes to apply and not a huge amount of technical experience, provided you're careful.. I'm sure there are howtos for it around here or google.

Unfortunately, if you question is how to detect your CPU temp, of that I'm not exceptionally knowledgable.

---

### Post by creedog on 2007-09-27
So what is the temp of your cpu if you just boot up straight into bios?
Let it sit for a while and then what is your temp?

---

### Post by tszanon on 2007-09-27
Is your computer clean inside? Maybe there's too much dust in the fans.

---

### Post by drsmaw on 2007-09-27
Creedog,
that is the temp if I restart and enter the bios.  I can't get a reading while using Ubuntu, which doesn't really matter to me.    
After a while, 20-25 minutes after shutdown, the bios reading of CPU temp was 56 degrees.  Obviously cooling down, the internal temp was reading 39 degreees.

I know this is not Windows, but i never experienced this using any windows platform on this computer.

So why do you think my temps are so high?  I have an external usb fan sucking any hot air out; yes, my computer is in one on those cpu tower cabinets.
But like i said, i never had this experience with XP or Vista.

---

### Post by drsmaw on 2007-09-27
tszanon

It's clean. I just had it out on Sunday and saw nothing worth cleaning. The desktop is only in use 2 months.

---

### Post by mcduck on 2007-09-27
That's quite normal temp for a P4. No need to worry about it :)

---

### Post by drsmaw on 2007-09-27
mcduck

Thanks for easing my mind.  But if 62 is quite normal, then what temp should I be worried at?

---

### Post by atlfalcons866 on 2007-09-27
Is your p4 a prescott core? if so they are known to get real hot

---

### Post by mcduck on 2007-09-27
> **drsmaw said:**
> mcduck

Thanks for easing my mind.  But if 62 is quite normal, then what temp should I be worried at?

Sorry, my mistake. I re-checked the max temps for P4 and it's a bit lower than I remembered. 62°C is still quite OK if it doesn't go much above that, and P4's are well known for their tendency to run very hot (They have HUGE thermal power, 100-130W compared to Core 2 Duo's 65W). But as the max recommended temperature is 70°C there's definitely some room for improvement.

You mentioned that the case and cooler are clean so that's not the problem. But your other sensors give  fairly high reading, at least one of those should be pretty close to case temperature and 45°C is way too much for that.. Do you have any case fans and how are they positioned?

Also, are you using the default Intel heatsink & fan? Default cooling solutions from both Intel and AMD are pretty awful (and noisy!) so replacing it with better one could easily drop your temperature 10°C which would take you fairly to the safe region.

---

### Post by tszanon on 2007-09-27
> **mcduck said:**
> Also, are you using the default Intel heatsink & fan? Default cooling solutions from both Intel and AMD are pretty awful (and noisy!) so replacing it with better one could easily drop your temperature 10°C which would take you fairly to the safe region.
A friend told me exactly the opposite: the cooler and heatsink that come with the processor are just what is needed for it to run in an acceptable temperature. It's not weak, so the temperature won't go above the limit, but it's not excellent, so there would not be too much room for the temperature to increase.

If they're noisy or not, I can't say. I think that AMD ships silent coolers, since I had a cooler some years ago that was annoyingly noisy.

---

### Post by mcduck on 2007-09-27
> **tszanon said:**
> A friend told me exactly the opposite: the cooler and heatsink that come with the processor are just what is needed for it to run in an acceptable temperature. It's not weak, so the temperature won't go above the limit, but it's not excellent, so there would not be too much room for the temperature to increase.

If they're noisy or not, I can't say. I think that AMD ships silent coolers, since I had a cooler some years ago that was annoyingly noisy.

Actually Intel even had some troubles at some point where their own heatsink couldn't cool some P4 models enough, which caused the CPU to throttle it's speed almost immediately if the CPU usage jumped to 100%.. So you could never get the full performance out of the CPU with it's own cooler. :D

No, they are not good coolers. They may be good enough if the case cooling is good or the CPU is not used at 100% for long times, but definitely you get lower temperatures _and_ less noise with better coolers. You can get clearly better coolers for less than 30€..

---

### Post by drsmaw on 2007-09-27
Excellent advice and I will utilize what has been said here.
But here lies another issue of fan speed control.  This thing is full tilt no matter what I do.  Now, I had no problems with pclos2007 or DSL.  How can I calm this fan down a little bit.  Obviously I am not stressing this thing at all, so why does it get hotter.
Like I have said, it never ran like this on any windows install either.
See, I like the ease of use in Ubuntu, mainly for my wife.  If there is a distro that might be just as easy with less problems, I'm listening.

---

### Post by drsmaw on 2007-10-06
Solved!   Using KPowersave for days and no problems.  CPU temp is normal and fan is quiet.  definitely recommend to use Kpowersave.

---

