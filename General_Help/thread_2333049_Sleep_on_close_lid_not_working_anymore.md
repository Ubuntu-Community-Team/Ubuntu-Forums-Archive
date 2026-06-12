---
title: "Sleep on close lid not working anymore"
date: 2016-08-06
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2016-08-06
i have used 14.04 since before it was fully released on this laptop (at least i think i did, is this system really over 3 years old already)
i have upgraded to 16.04; kernel: 4.6.3-040603-generic
it has always entered sleep mode when i closed the lid in the past, i just noticed it did not when my audio kept playing over bluetooth and i was thought how is that possible during sleep mode
*using mains power not battery

---

### Post by ajgreeny on 2016-08-06
I had the similar problem with an old netbook with a bad battery.  I originally had it set to hibernate when lid closed and running on battery, which was essential with the poor battery, but to suspend when plugged in.

The only way I could get it to do what I wanted was to make the settings the same irrespective of which power supply was in use.

It might be worth looking into your settings in detail.

PS:
Your profile info on the left of my screen says you are still on Xubuntu 13.04 Raring Ringtail; you might wish to update that.

---

### Post by pqwoerituytrueiwoq on 2016-08-06
unable to find that setting, but i tried to set my flavor as xubuntu but i get a 403 error when i try to save
i was looking in the power manager settings i did not see a lid close event or a when on/off battery option (battery is not connected)
where is the config file? probably better off editing that manually

edit: after a reboot it is acting like normal :? wonder if bluetooth caused it (nope, unable to reproduce)
now lets see how the 4.7 kernel is working after another one

---

