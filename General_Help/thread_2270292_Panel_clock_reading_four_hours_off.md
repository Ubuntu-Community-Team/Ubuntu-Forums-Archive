---
title: "Panel clock reading four hours off"
date: 2015-03-21
forum: General Help
---

### Post by oaxacamatt1 on 2015-03-21
The clock on my panel is off by FOUR hours.  I have been to the settings to see if it is a settings issue BUT no.  When I go to the settings the time is set correctly.  When I go to the bios (during boot up) the time is also set correctly. Hmmm.  But when all that is set I still get a time that is four hours ahead.  I have checked the time zone and it is set correctly.  I even found some reference to some file in /etc and set the UTC = yes, but this does not change it either.

BTW, I am running Xubuntu 14.04.2 on a 'very std' Gateway, which has had different versions of Ubuntu for years now with no problems.

I have looked around the forums and am a little stomped.  I was starting to think that the cmos battery was dead but that is not it either.

Any suggestions would be very helpful,
M

---

### Post by kerry_s on 2015-03-21
did you add ntp & switch it to internet sync ?

---

### Post by oaxacamatt1 on 2015-03-21
Yes, I think that is when it all started but I cannot straighten it out.  I have had it on both manual and internet sync, one time or anouther.  Very puzzingly.   One more strange item is that when i log in it shows the correct time on the log in screen but when the home screen comes up it is off 4 hours.
hmmm

---

### Post by kerry_s on 2015-03-21
tried removing & putting back on panel ?
there's also another applet called xfce4-datetime-plugin, not installed by default, maybe give that a try.

---

### Post by HermanAB on 2015-03-22
Right click on the clock, go to Time Zone, untick UTC and tick your local time zone, then click Apply.  The stupid thing can have multiple zones selected and it will randomly use one of them to display the time.

---

### Post by kerry_s on 2015-03-22
> **HermanAB said:**
> Right click on the clock, go to Time Zone, untick UTC and tick your local time zone, then click Apply.  The stupid thing can have multiple zones selected and it will randomly use one of them to display the time.

you know were talking xubuntu here ?

---

### Post by lisati on 2015-03-22
> **kerry_s said:**
> you know were talking xubuntu here ?

Is the time zone "Pacific/Honolulu" correct?

---

### Post by kerry_s on 2015-03-22
> **lisati said:**
> Is the time zone "Pacific/Honolulu" correct?

yeah for me, i'm not the op though, the pics were to show there is no utc setting.

---

### Post by lisati on 2015-03-22
> **kerry_s said:**
> yeah for me, i'm not the op though, the pics were to show there is no utc setting.

Ah, my bad :( I think I need a coffee. :D

---

### Post by kerry_s on 2015-03-22
> **lisati said:**
> Ah, my bad :( I think I need a coffee. :D

your good, you saw it perfectly fine. enjoy a coffee all the same, i got 6 cups brewing myself. ;)

---

### Post by mcduck on 2015-03-22
if you see the correct (local) time in BIOS, then you should set the UTC  to "no" in */etc/default/rcS* (as your system clock clearly isn't running in UTC time).

---

### Post by oaxacamatt1 on 2015-03-22
Yes i worked it out.  

First to mcduck you are correct that setting the UTC to no helped

but 

I found a workaround.  
I deleted the standard clock that Xubuntu had in the panel and filled it with the Orage Clock settings instead and it works just fine now.

---

### Post by kerry_s on 2015-03-22
> **oaxacamatt1 said:**
> Yes i worked it out.  

First to mcduck you are correct that setting the UTC to no helped

but 

I found a workaround.  
I deleted the standard clock that Xubuntu had in the panel and filled it with the Orage Clock settings instead and it works just fine now.

i totally missed that clock, best part for you is it's already installed. lot's of settings to play with to. i call that a win win. ;)

---

