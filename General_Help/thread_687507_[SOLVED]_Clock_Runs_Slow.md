---
title: "[SOLVED] Clock Runs Slow"
date: 2008-02-04
forum: General Help
---

### Post by Falcorian on 2008-02-04
My clock has recently taken to losing about a minute an hour in 7.10. It boots with the correct time (or whatever time I shut it down / rebooted with). It worked fine for months, and then all of a sudden I wake up and it's 5 minutes behind. The only new package I installed (other than normal updates) right before the issue started was a python library (optparse).

I thought it might be hardware so I ran windows for a few days straight (and thank god that's over!) and it didn't lose so much as a second (with Internet syncing off).

When I click on the Clock and select 'Adjust Data & Time' it doesn't ask me for a password which seems odd. Once in the screen, I do not have the option to 'Synchronize Now' as show in my screenshot.


I've read through all the previous threads I could find and none seemed applicable, so I'm really lost now. Any one have suggestions?

Thanks!

---

### Post by Falcorian on 2008-02-06
I found a 'solution' to the greyed out box [here](http://ubuntuforums.org/showthread.php?t=679857).

I was also able to remove the symptom of my problem by adding more NTP servers to sync to. However, I don't know why it stopped working in the first place, nor why it started losing time so badly.

---

### Post by lespaul_rentals on 2008-02-06
> **Falcorian said:**
> I found a 'solution' to the greyed out box [here](http://ubuntuforums.org/showthread.php?t=679857).

I was also able to remove the symptom of my problem by adding more NTP servers to sync to. However, I don't know why it stopped working in the first place, nor why it started losing time so badly.

Try replacing the CMOS battery.

---

### Post by barney_1 on 2008-02-08
I agree, sounds like your CMOS battery is running out of juice.  It's usually a CR2032 battery, easy to find in most stores and also easy to replace.

---

### Post by forrestcupp on 2008-02-08
I don't think it's the CMOS because he said it's right after he reboots, and it never lost any time in Windows. It appears that the CMOS is right, but the time within Linux becomes wrong.  It looks like he already found the culprit and took care of it.

---

### Post by Falcorian on 2008-02-12
> **forrestcupp said:**
> I don't think it's the CMOS because he said it's right after he reboots, and it never lost any time in Windows. It appears that the CMOS is right, but the time within Linux becomes wrong.  It looks like he already found the culprit and took care of it.

Yep. It wasn't the CMOS as I think I made clear through the "It's fine on reboot" and "Windows works fine without synching". 

NTP had somehow incorrectly set my drift, and then the server I was using went down so it never corrected. Trying new servers fixed it.

---

