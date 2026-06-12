---
title: "100% after idle?"
date: 2007-03-31
forum: General Help
---

### Post by Shmifty on 2007-03-31
If I leave my computer alone for more than 30 minutes the cpu usage sometimes jumps to 100% and stays there.

I use Kubuntu Edgy KDE 3.5.6 Kernel 2.6.17-10-386

---

### Post by acormack on 2007-03-31
open up a terminal and type top

see which processes are using most cpu

if it is acpi  then the power management daemon is the culprit

type 

sudo /etc/init.d/acpid stop

then see what cpu load is

---

### Post by acormack on 2007-03-31
duplicate post - deleted

---

### Post by Shmifty on 2007-03-31
I've tried that, unfortunately the load is apparently so much I cant even open up a terminal to find the culprit let alone stop it.

---

### Post by acormack on 2007-03-31
Does ctrl+alt+F1  allow you to log in?

if not then I suggest you try disabling ACPI from the system settings, system services menu.

Then keep your fingers crossed!


Alec

---

### Post by Shmifty on 2007-04-04
I was able to find out that Xorg was using 70%+ of my cpu. I would just like to clarify that this happens when I leave my computer alone (not when I put my computer on standby)

---

### Post by Shmifty on 2007-04-05
Bump for possible explanation

---

### Post by GoldNugget on 2007-04-05
I had a similar problem with my cpu shooting up to 100% when idle. I found it was Beagle endlessly indexing files in the background. Try killing Beagle in the System Monitor and uncheck in Beagle preferences to 'automatically index files'. This worked for me, until reboot. Anyone know how to keep it from coming back?

---

### Post by acormack on 2007-04-05
Are you able to paste the output from the top command here so we can have a look.

Does it ever happen while you are using the computer or is it only when idle?

What screensaver settings do you have.  How long idle does it take before it kicks in?  Is it possible to disable it?

---

### Post by CocoAUS on 2007-04-05
I, too, was experiencing this problem.  I leave my PC on at night, and when I wake up, it takes a minute or two for the computer to actually respond to my actions.  I, too, found this to be Beagle running in the background, apparently trying to take advantage of the PC's idle time to do its indexing.  I removed Beagle and installed Tracker, and the problem disappeared (though I now have problems using Tracker).

I suggest turning off Beagle completely, at least once as a test.

---

### Post by Shmifty on 2007-04-05
Well it just happened again (unfortunately this time I was not able to do top, even by alt-ctrl-F1). I know it can't be beagle, as I don't even have that program installed. I just have a blank screensaver set to run after 30 minutes, nothing special. Also I don't know if this is any consolation, but I can't even edit my monitor and display in administrator mode for some reason.

---

### Post by Shmifty on 2007-04-05
the bump because I have a feeling this can be answered.

---

