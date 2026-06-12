---
title: "suspend and hibernate on an hp dv9200"
date: 2007-11-30
forum: General Help
---

### Post by kefurd06 on 2007-11-30
i know there are only a thousand posts about suspend/hibernate, but this is killing me. ubuntu is not a solid replacement OS for notebooks until it can faithfully suspend/hibernate. i never thought twice about closing my lid in vista, packing up and walking to my next college class. now with ubuntu, i have two options: shut down and boot when i get to the next class (bootup is time-consuming especially now that gutsy login takes so long)  or i can spin the wheel. maybe the system will suspend and resume properly, maybe not. 

suspend/resume is a function that should JUST WORK. i've trolled the forums off and on, an hour at a time for weeks now, testing different 'workarounds' and i've got nothing. 

so is this it? do i tell people 'ya i love it, but it's not ready for laptops yet'. i mean it's bad enough to have to crawl pages and pages of posts but even then i find nothing that helps.

---

### Post by kefurd06 on 2007-12-02
so i guess there's my answer.

---

### Post by flashbackk on 2007-12-02
I'm with you.  I am the biggest fan of ubuntu there is and I am confused.
Historically, an update would fix my problem and that would be it.  Like the dummy I am
I get up every morning thinking this is the day.    Nothing.  I took suspend for granted and I am mad I can't use it now.  Laptops are useless this way.

---

### Post by vivichrist on 2007-12-02
which graphics chipset do you have?

what measures have you taken? ...etc

---

### Post by kefurd06 on 2007-12-02
me? nvidia geforce go 7600. i've tried several workarounds/fixes posted in the forums, including downloading a different suspend program (hang on use), and tweaking some suspend/hibernate settings (warm boot video card, vesa usage, etc).

---

### Post by vivichrist on 2007-12-03
the pm-utils package worked for me, keep the nvidia acpi tweaks and try experimenting with the /usr/share/hal/fdi/information/10freedesktop/20-video-quirk-pm-hp.fdi file and create you own <match...><merge...></merge></match> lines.
requires reboot.

---

### Post by kefurd06 on 2007-12-03
thanks for the suggestion. in device manager i've got a lot of unknowns (vendor, device, bus type, etc). where do i look up system.hardware.vendor and system.hardware.version?

Whoops. just found it under the advanced tab.

how do i know if pm_utils is being used? also, suspend hasn't failed yet, but i can't hibernate at all now. (hangs at blank screen upon hibernating). also when i come off suspend 9 times out of 10 my wireless network is hosed. sometimes NetworkManager will show 100% CPU usage. any fix for that?

---

### Post by vivichrist on 2007-12-11
try with and without pm-utils. the order of which suspend/hibernate utility used is in a file somewhere /usr/lib/hal...

---

