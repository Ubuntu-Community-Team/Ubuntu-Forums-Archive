---
title: "Ubuntu trys to suspend and fails"
date: 2007-06-12
forum: General Help
---

### Post by Trab on 2007-06-12
Hello, I've been using Ubuntu since Warty, but about March, my SATA hard drive failed, I was able to get part of my home directory to my network drive, and it took me a while to finally get a new drive and install Feisty.


I had some power issues, my new drive used SATA power, with no option for IDE power, but I figured that out...

however, its still having problems. 

Despite the fact that in gnome-power-preferences I have it never put the computer to sleep, and only turn of display after 25 minutes, if i leave it for long periods of time, it will try to suspend, fail, and turn off. turning it back on, it trys to boot, fails, and needs to be reset again.


I'm not sure where this option needs to be set, but its something i would like to fix.

cheers,
Trab

---

### Post by Trab on 2007-06-13
for any other users who have this problem, I used gconf editor and went through applications to gnome-power-preferences and changed all instances of "suspend" to "nothing"

I have no idea if that will help, but I'm hoping it will disable whatever is trying to use suspend.

cheers,
Trab

---

### Post by trippinnik on 2007-06-13
can you list your hardware?  as well as the output of the command 'dmesg' in the terminal.

---

