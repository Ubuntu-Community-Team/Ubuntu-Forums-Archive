---
title: "Desperatly Need An Expert!"
date: 2008-01-09
forum: General Help
---

### Post by Kemrin on 2008-01-09
I'm running Ubuntu 7.10 on a Dell XPS M1210

I plugged a Samsung 150s into my computer's moniter port, and used a tool to try to make it the Default moniter. My attempt caused strange behavior in the xserver, by which i mean it didn't activate the samsung moniter, and it went to low graphics mode. Then, i tried to change it back to normal, but accidentally made it worse. Now I can't start the xserver. I need to know how to restore the defaults using a terminal interface.

Please help me!!

---

### Post by PinkFloyd102489 on 2008-01-09
Boot into the recovery shell and cd to /etc/xorg/.

Find the backup copy of xorg.conf, probably named xorg.conf.bak or something similar.

Copy the backup over the original using "cp xorg.conf.bak xorg.conf"

Then type "startx".




This should fix it.

---

### Post by benrboone on 2008-01-09
you can reconfigure your xserver by doing this and answering the questions most of the question should be just be default (enter)

sudo dpkg-reconfigure xserver-xorg

If you have a backup of your xserver config file you could also restore that by renaming it

---

### Post by az on 2008-01-09
> **benrboone said:**
> you can reconfigure your xserver by doing this and answering the questions most of the question should be just be default (enter)

sudo dpkg-reconfigure xserver-xorg

If you have backup our xserver config file you could also restore that by renaming it

Boot into recovery mode first and then run

dpkg-reconfigure -phigh xserver-xorg

You don't need to use sudo from recovery mode.  The -phigh argument skips most (if not all) of the questions.  It's simpler that way.  Running the recofigure script automatically makes a backup (timestamped in the file name) of your xorg config, so there is no need to copy it by hand.

---

### Post by Kemrin on 2008-01-09
Thank you very much. My Xserver is back up and running. I very much appreciate it ^_^

---

### Post by benrboone on 2008-01-09
good to known about the -phigh option.  What exactly does it skip?

---

### Post by TheWizzard on 2008-01-09
good to hear your problem is solved.

i'd advice to backup both /home and /etc. 

this way you can always restore all important settings. 
the /etc backup is also a good reference after an upgrade to a newer ubuntu. saved me a couple of times ;-)

---

