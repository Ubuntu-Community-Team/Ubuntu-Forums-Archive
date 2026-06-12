---
title: "back up"
date: 2007-12-13
forum: General Help
---

### Post by mr.farenheit on 2007-12-13
have a problem that can hopefully be solved. i love ubuntu and its the only thing i will run. my problem is i have no current internet connection. i've had to reformat several times due to technical failure and its hard for me to constantly bum off of a friends internet long enough to run a reinstall process and get my computer back up and running to the way i want it. is there any method of creating a complete backup of the system or at least a way for me to back up the programs i have installed so that i can reformat and start from scratch without an internet connection?

---

### Post by lswest on 2007-12-13
best method would be [ here ]("http://ubuntuforums.org/showthread.php?t=564836") and i know for a fact, cuz i used it to restore Ubuntu just a couple of days ago after Paragon partition manager corrupted it while trying to resize it XD really should use GParted for that lol.

---

### Post by Irihapeti on 2007-12-13
If you want a complete snapshot of your system, you can use Partimage, which is on the GParted liveCD, and no doubt elsewhere as well. Some say that the .gzip compression option doesn't work. I've used the .bz2 option successfully to replace my system after I wrecked it.

---

### Post by mocoloco on 2007-12-13
A very simple way would be to use AptOnCD.  It's in the repositories.  It will basically let you save everything you have in /var/cache/apt/archives (eveything synaptic/apt/aptitude has installed) and put in on a CD/DVD.  If you have a separate /home partition it's an easy way to go.

---

