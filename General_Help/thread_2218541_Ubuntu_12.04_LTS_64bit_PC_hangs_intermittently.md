---
title: "Ubuntu 12.04 LTS 64bit PC hangs intermittently"
date: 2014-04-21
forum: General Help
---

### Post by galapogos on 2014-04-21
Hi,


I have a Ubuntu 12.04 LTS 64bit PC that I upgraded to from Ubuntu 10.04 LTS 64bit quite some time ago. I've been noticing sporadic system hangs and I can't figure what exactly is causing it. The PC simply stops responding, and requires a system reset. Are there any logs that survive the reboot that might let me know what exactly caused the hang and what I can do to fix it?


Thanks.

---

### Post by ajgreeny on 2014-04-21
Does the complete OS freeze or just the GUI?
If you can Ctrl+Alt+F1 to get to a command line and login to that you can view the various log files in /var/log using ```
less /var/log/syslog
less /var/log/dmesg
less /var/log/Xorg.0.log
```one by one to see if anything useful shows.

Using **less** to view the files allows you to scroll using the cursor keys in the command line, which you can not do if you use **cat**

---

### Post by galapogos on 2014-04-21
I'm not sure since I haven't tried Ctrl-Alt-F1, but I suspect so, because my keyboard is unresponsive (numlock/capslock/scrolllock don't toggle).

If the entire OS freezes, what are my options?

---

### Post by ajgreeny on 2014-04-22
If the keyboard is frozen this may not work but you can try holding **Right-Alt+Print-Screen** and then slowly type **reisub** with about 1 second between key presses,  That may reboot the system, but it does depend on key-presses being detected.

Definitely worth  try!

---

### Post by galapogos on 2014-04-24
> **ajgreeny said:**
> If the keyboard is frozen this may not work but you can try holding **Right-Alt+Print-Screen** and then slowly type **reisub** with about 1 second between key presses,  That may reboot the system, but it does depend on key-presses being detected.

Definitely worth  try!
As it turns out, the keyboard is frozen, so I can't do anything. Are there any logs that persist after a reboot that I may look at to look for clues as to what's causing the system hang?

---

### Post by ajgreeny on 2014-04-24
Not sure!

have a look at the numbered .gz archived versions of the log files I mentioned in post 2; you may find something there, though I am not sure if those logs will be saved if the whole system crashes.

---

### Post by efflandt on 2014-04-25
If you have not done so, install **openssh-server**, or more simply install **ssh** which is a meta package of client (already installed by default) and server. When it hangs see if you can connect to that computer with ssh (or PuTTY in Windows).

I had strange hangs years ago when a video card was failing. At random times the keyboard and mouse clicks would become unresponsive, although, mouse cursor could usually still move. Attempting to ssh into the computer could tell you if then entire computer is hung, or just something with keyboard or video. And if you can get in that way you could check dmesg (**dmesg | less**) for anything unusual.

---

