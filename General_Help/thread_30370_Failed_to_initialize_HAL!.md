---
title: "Failed to initialize HAL!"
date: 2005-04-28
forum: General Help
---

### Post by Das Ein on 2005-04-28
every time recently I turn on my computer I get a 
"failed to initialize HAL!" error.
When my computer is booting up everything says it is ok, nut I get that error. What is my problem?

---

### Post by artinla on 2005-04-29
I had the same problem, but nobody ever figured it out.

I had no device manager, and the drive icons that pop up when you add a drive or CD no longer worked.  

I did find that if I waited a minute or two and restarted dbus TWICE, things would work normally again, until I rebooted.

I made a script that I could run from a launcher, and it had to be run in a terminal.  I just sent the terminal to another workspace once the script was completed.

#Begin Script
sudo /etc/init.d/dbus-1 restart
wait
gnome-volume-manager
#End Script

I know it is a hack, but it is better than nothing at all.

Art

---

