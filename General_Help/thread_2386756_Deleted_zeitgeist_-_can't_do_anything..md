---
title: "Deleted zeitgeist - can't do anything."
date: 2018-03-09
forum: General Help
---

### Post by 611devonn on 2018-03-09
After purging everything zeitgeist, I get the login screen, am able to log in, then everything but the wallpaper is gone. No manner of clicking, right-clicking, or key combinations have any affect.  I've tried sudo apt-get in restore mode, but get errors the us.ubuntu.com is not reachable, even though I've run commands to start networking, etc. I'm running 16.04 and don't have a disk. I'll gladly reinstall Unity/zeitgeist just to have my computer back. Any help? Thanks

---

### Post by QIII on 2018-03-09
Hello!

That sounds like a pretty pickle!

Exactly what steps did you take to remove zeitgeist?

---

### Post by 611devonn on 2018-03-10
I followed steps to list all zeitgeist, then purge all, as in:  sudo apt-get purge python-zeitgeist  
which included all zeitgeist; rhythmbox, libzeitgeist, zeitgeist, zeitgeist core, etc

---

### Post by monkeybrain20122 on 2018-03-10
Why did you want to remove zeitgiest?? Now you have broken your desktop completely. Probably reinstalling is the only route if you can't even reach the server.

---

### Post by 611devonn on 2018-03-10
I wonder myself what I was thinking. Not clearly, that's for sure.

---

### Post by vanadium on 2018-03-10
"sudo apt install ubuntu-desktop" should restore things, I guess. You only need to be able to reach a terminal. While your are in the login screen, switch to a virtual console using Ctrl+Alt+F3, log in and issue the command.

---

### Post by 611devonn on 2018-03-10
Solved.  Here are the commands I ran from Ctrl + Alt + F1:
sudo apt-get install --reinstall ubuntu-desktop

sudo dpkg --configure -a" first. 

sudo apt-get install --reinstall ubuntu-desktop

sudo apt-get -f install

sudo apt-get install --reinstall ubuntu-desktop

Then rebooted and everything seems fine.  Thanks for the help.

---

### Post by vanadium on 2018-03-11
We cannot know currently, but if your package system was not broken (I did not catch any signal it was), then "sudo apt install ubuntu-desktop" probably would have been sufficient. Removing zeitgeist removed ubuntu-desktop among many other things, so reinstalling that metapackage ubuntu-desktop is sufficient to pull all essential desktop components back in.

---

