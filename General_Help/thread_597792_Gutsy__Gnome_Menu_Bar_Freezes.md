---
title: "Gutsy : Gnome Menu Bar Freezes"
date: 2007-10-30
forum: General Help
---

### Post by MarinaraOfDeath on 2007-10-30
I'm loving Gutsy, but I've started encountering the inevitable problems. I'm just happy because there are so many fewer of them to fight than there was with a fresh Dapper install. Here's the one I'm really stumped with, and there doesn't seem to be anything quite like it so far in the online world. 

I'm experiencing Gnome menu bar freezes. This started sometime yesterday. Here's my symptoms:
[LIST=1]
[*] The clock stops changing
[*] Ctrl+Alt+Del reboots the system instead of pulling up the log-out/shutdown menu
[*] The fan runs for 10-15 minutes, stops for a bit, then repeats the cycle
[*] The main menu is frozen; nothing pops open from the tray
[/LIST]
The three main things I did yesterday were
[LIST=1]
[*] Installed virtualbox to try and virtualize my dual-boot windows XP partition (this failed miserably, so virtualbox has been removed after I repaired my windows installation).

[*] Changed permissions on two physical partitions (/media/sda1 and /media/sda2) while trying to do this (the system somehow reverted these itself, though I get a boot log error about /media/sda2 being already mounted.).

[*] Installed and configured wine so that I can run the one piece of software I can't use/substitute in linux (tis better to have installed and lost the disk than to never have installed at all...).

[*] Install Inkscape to make a couple of svg graphics to use as logos for my own scripts on the panel.
[/LIST]
I have terminal mapped to a keyboard combo, so I was able to recover from an episode of this earlier today with 
```
sudo /etc/init.d/gdm restart
```
but that's a rather annoying workaround since everything has to be saved and reopened after logging back in. I'd rather solve the underlying problem if it can be diagnosed.

Any ideas?

---

### Post by MarinaraOfDeath on 2007-11-05
Top told me that the problem was gnome-panel taking 95% or more cpu time. After more googling and futzing around, looks like the problem, looks like the problem is transparency on the taskbar/main menu bar. I turned that off and set them to autohide, no problems since (so far, knock on wood).

---

