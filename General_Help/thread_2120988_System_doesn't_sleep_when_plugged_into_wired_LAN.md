---
title: "System doesn't sleep when plugged into wired LAN"
date: 2013-02-28
forum: General Help
---

### Post by Objekt on 2013-02-28
Using Ubuntu 12.04.2 (x86) on my Samsung notebook.  When the system is operated with wireless networking, the power-saving features (e.g. sleeping after x minutes) work normally.  However, I've noticed that when I have it plugged into wired LAN at home (which I use because the speed is so much better for copying files within my network), the system doesn't ever enter sleep.

How do I fix this?  I suspect the system is receiving traffic over the LAN port that makes it think it should stay "awake."

---

### Post by plucky on 2013-03-01
Enter your BIOS and disable WOL (Wake on Lan)


Good Luck

---

### Post by Objekt on 2013-03-01
There isn't any such option.

---

### Post by Toz on 2013-03-01
Try another sleep/resume while wireless followed by a sleep/resume attempt while wired, then post back the contents of your /var/log/pm-suspend.log file like this:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.

---

### Post by Objekt on 2013-03-01
Naturally, when I tried to reproduce the problem, it didn't occur.

I know the machine did stay on all night a couple of nights in a row, so I'm not sure what's really going on.

---

### Post by Objekt on 2013-03-02
I have a clue now.  It appears that the problem may have something to do with VLC Media Player.  I had it open - although not with a video or audio file being played - last night when I left the machine alone.  And it did not suspend, even after hours of sitting there (it should suspend after 10 minutes of inactivity).  Could be a bug in VLC Media Player, or in whatever process tells the OS whether it's allowed to suspend.

---

### Post by Toz on 2013-03-02
I don't have vlc installed here, but isn't there an option in the settings to prevent the computer from screen dimming/suspending if its running? 

Also see: [http://askubuntu.com/questions/118713/why-does-a-stopped-vlc-inhibit-suspend]("http://askubuntu.com/questions/118713/why-does-a-stopped-vlc-inhibit-suspend").

---

