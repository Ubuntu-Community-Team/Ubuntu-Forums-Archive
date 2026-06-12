---
title: "Bash Script Help"
date: 2013-01-24
forum: General Help
---

### Post by doppel.ganger on 2013-01-24
Hey all,

I'm using an Arch Linux system for a small private Minecraft Server. I'm using custom MC Server software called Bukkit. I'm using the development builds, so there are frequent updates. Which means every time there's an update, I have to delete the old jar and download the new one. I decided to try to make a simple script that would automatically delete the old one and download the newer version. The problem is, I don't know how to make wget (or curl) check to see if there is a new version of the jar. The name of the jar itself doesn't change, but the directory it's under does. The builds are at [http://dl.bukkit.org/downloads/craftbukkit]("http://dl.bukkit.org/downloads/craftbukkit"). Can anyone help me with this? Thanks!

Thomas

---

### Post by Toz on 2013-01-24
Moved to General Help.

---

### Post by papibe on 2013-01-24
Hi doppel.ganger.

If I remember correctly, the jar file is not too big, so without putting too much thought on it, I think something like this would work:
[LIST]
[*]Make an schedule to download regularly the jar (use crontab for instance).
[*]Use the command 'diff' to compare them.
[*]If they are different, it means it's new version, so you can replace the current one with the recently downloaded.
[/LIST]
Just a thought.
Regards.

---

### Post by Vaphell on 2013-01-25
```
wget http://dl.bukkit.org$( wget -q -O- http://dl.bukkit.org/downloads/craftbukkit/ | grep -oE '/downloads/[^"]*-dev.jar' | head -1 )
```
should download the latest *-dev version

---

