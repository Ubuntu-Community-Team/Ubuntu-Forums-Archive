---
title: "My screen goes black after a few seconds ubuntu 12.10"
date: 2012-10-30
forum: General Help
---

### Post by Salvagluque on 2012-10-30
Hi guys,

Well here's the deal. I upgraded a week ago to the ubuntu 12.10 version. Turns out everything was fine until yesterday when my screen started to go black after merely 30/40 seconds.

I went to the bettery/power app. put suspend whe inactive for in don't suspend and show battery never, is a desktop.

Then went to brightness and lock and set the turn screen off when inactive for option in never, and lock the screen in off.

rebooted the computer but still the system keeps going black in a few seconds, and suspends the system in about an hour.

Thanks in advance.
Salvador

---

### Post by Salvagluque on 2012-10-30
basically I did this but in ubuntu 12.10. The names change but is exactly that and didn't work.

[http://www.liberiangeek.net/2011/10/ubuntu-screen-going-blank-dark-on-you-stop-it-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/10/ubuntu-screen-going-blank-dark-on-you-stop-it-in-ubuntu-11-10-oneiric-ocelot/)

---

### Post by danelwillis on 2012-10-30
try playing with power setting by adjusting the brightness and power controls

---

### Post by Salvagluque on 2012-10-30
Already done that and there is nothing changed. I think I may need to change the grub or someother configuration from root or something.

---

### Post by wojox on 2012-10-30
Install [Caffeine]("https://launchpad.net/~caffeine-developers/+archive/ppa") and be done.

---

### Post by critin on 2012-10-30
i just thought of a possibility.  Did you install an automatically changing background app. before this started?  or/  Did you change screensaver settings?

---

### Post by Salvagluque on 2012-10-30
I don't know if the problem was there before or after putting one of the default autochanging walpapers. Anyway, I chosed another wallpaper, but the problem persist.

I haven't installed an app to change backgrounds.

---

### Post by critin on 2012-10-30
> **Salvagluque said:**
> I don't know if the problem was there before or after putting one of the default autochanging walpapers. Anyway, I chosed another wallpaper, but the problem persist.

I haven't installed an app to change backgrounds.

edit:  OK, You did NOT install an app.   The default shouldn't cause this.


The best idea is from [wojox]("http://ubuntuforums.org/member.php?u=802919") at post #5.

---

### Post by Salvagluque on 2012-10-30
I already installed caffeine. I had to install it via the terminal, because the software center or the synaptic didn't bring up anything. But i don't know what to do next. I tried sudo caffeine, but nothing.

---

### Post by critin on 2012-10-30
Did you install the PPA from that link?  I assume you searched the dash?

---

### Post by Salvagluque on 2012-10-30
Yep, I installed the caffeine ppa´s and after I installed caffeine from theterminal.

Something funny, is that even when I play videos the screen gors blak in seconds anyway.

---

### Post by varunendra on 2012-10-30
> **Salvagluque said:**
> Then went to brightness and lock and set the turn screen off when inactive for option in never..There is a checkbox below that option that says "Dim screen to save power" Uncheck that as well.

---

### Post by Salvagluque on 2012-10-31
I searched for the checkbox, it doens seem to be there. At least not in my computer.

---

