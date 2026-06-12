---
title: "Who starts Evolution?"
date: 2014-04-25
forum: General Help
---

### Post by oz1cz on 2014-04-25
I don't normally use Evolution, but a few days ago I started it by accident. And now part of it always starts up every time I log on. A ps -ef shows these processes running:

[FONT=lucida console]UID        PID  PPID  C STIME TTY          TIME CMD[/FONT]
[FONT=lucida console]claus    20008 19711  0 15:08 ?        00:00:00 /usr/lib/evolution/evolution-source-registry[/FONT]
[FONT=lucida console]claus    20074 19711  0 15:08 ?        00:00:00 /usr/lib/evolution/evolution-calendar-factory[/FONT]
[FONT=lucida console]claus    20396 19812  0 15:09 ?        00:00:00 /usr/lib/evolution/3.10/evolution-alarm-notify[/FONT]

How do I get rid of them? I tried running gnome-session-properties, but it does not list Evolution as a program it starts. I cannot see Evolution in .config/autostart.

In the above process list, process 19711 is "init --user", and process 19812 is "gnome-session --session=ubuntu".

---

### Post by mcduck on 2014-04-25
Some evolution components are used by Gnome's calendar (the one you can access through the clock on your panel), so they are running by default. That does not mean that the Evolution itself would be running.

---

### Post by ibjsb4 on 2014-04-25
Since I do not use it, my solution was to just remove evolution.  Note, this is what works in 12o4 and should work for you.

Do not remove evolution-data-server or evolution-data-server-common as they are needed for other system functions.

[http://askubuntu.com/questions/32231/how-can-i-remove-the-evolution-package-completely](http://askubuntu.com/questions/32231/how-can-i-remove-the-evolution-package-completely)

[http://www.google.com/search?client=qupzilla&q=remove%20Evolution%20ubuntu](http://www.google.com/search?client=qupzilla&q=remove%20Evolution%20ubuntu)

---

### Post by oz1cz on 2014-04-25
Okay, I've probably made a mistake here. What really bothers me is that the envelope icon in the notification area now contains information from both Thunderbird (which I use) and Evolution (which I do not use). The Evolution notification is new, and I want to get rid of it.

I (wrongly, apparently) assumed that the three Evolution processes were the source of the notification.

So my question should probably be rephrased thus: How do I remove Evolution notifications from the envelope icon in the notification area?

---

### Post by oz1cz on 2014-04-28
> **oz1cz said:**
> So my question should probably be rephrased thus: How do I remove Evolution notifications from the envelope icon in the notification area?

I found the answer here: [http://askubuntu.com/questions/449174/email-icons-missing-from-menu-bar-after-upgrade-to-ubuntu-14-04](http://askubuntu.com/questions/449174/email-icons-missing-from-menu-bar-after-upgrade-to-ubuntu-14-04)

---

