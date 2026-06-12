---
title: "Excessive battery drain on suspend"
date: 2021-09-09
forum: General Help
---

### Post by davy jones on 2021-09-09
I've recently installed Ubuntu 20.04.3 on a new Dell Vostro 3500 (11th gen processor). Ever since I did this, the battery is draining way too much while on suspend (~5-6% per hour). The output for cat /sys/power/mem_sleep is [s2idle]. Even after following the instructions to change it to s2idle [deep] from [here]("https://learnubuntumate.weebly.com/draining-battery.html"), the output is still [s2idle]. I'm certain that there is no issue with the hardware because I was using Windows 10 for 2 months on this with no issues.


I'm not sure if this is relevant, but I copied my entire /home folder including the hidden files and folders for settings to my new laptop from my old one to preserve my settings (don't know if that could be causing this; if it is then I would appreciate help on how to fix this because I'm assuming you can't just delete setting files).


Another thing is that changing settings by editing files in my / folder has not worked for another issue ([screen does not go blank when lid is closed]("https://ubuntuforums.org/showthread.php?t=2466870"))

---

### Post by GhX6GZMB on 2021-09-09
> **davy jones said:**
> 
I'm not sure if this is relevant, but I copied my entire /home folder including the hidden files and folders for settings to my new laptop from my old one to preserve my settings (don't know if that could be causing this; if it is then I would appreciate help on how to fix this because I'm assuming you can't just delete setting files).


This is a bad idea. The hidden settings files in $HOME are in a lot of cases hardware dependent, you can't just copy them from one machine to another.

---

### Post by davy jones on 2021-09-10
I reset using dconf reset -f / and even deleted a bunch of files that were older than my install (i.e transferred from the previous laptop), but this has not fixed the issue. Battery is still draining very fast, even on suspend. This is despite having tlp installed.

---

### Post by GhX6GZMB on 2021-09-10
Well, at least dconf reset -f / should have cured the setting files problem.

Is your machine is actually suspending or just blanking the screen? I have no experience with Dell Vostro, but on HPs the power LED blinks when the machine is suspended. Perhaps check the user manual if the Dell also shows this state somehow.

Another possible issue (again manufacturer dependent): some PCs keep powering external USB devices during suspend. This needs to be checked as well.

---

### Post by davy jones on 2021-09-10
I'm fairly certain it suspends because this isn't from closing the lid but actually hitting suspend. And I can see the WiFi connecting when the system wakes. Is there a command I can run to confirm it?

---

