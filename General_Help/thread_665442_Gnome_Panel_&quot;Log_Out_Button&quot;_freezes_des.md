---
title: "Gnome Panel &quot;Log Out Button&quot; freezes desktop"
date: 2008-01-12
forum: General Help
---

### Post by denali on 2008-01-12
When ever I press the "Log Out Button" on Gnome Panel, my desktop freezes.  I can't click on any thing.  I waited for several minutes to see if it was simply a slow running task, but nothing comes up.  Only thing I can do is to hit CTRL-ALT-Backspace.

Any ideas?

---

### Post by cmnorton on 2008-01-12
Do you have another system that you could use to ssh or telnet into this frozen system? You'd need to download and install sshd or telnetd, start them running; and take note the ip address of the system about to be frozen.

Then, you could get some info out of the logs like dmesg, /var/log/syslog and /var/log/messages and post them here.

Also, have you reported this as a bug in launchpad?

---

### Post by Fatman_UK on 2008-03-10
I get this with my system at work, but the machine isn't actually locked up. it just takes ages to bring up the dialog with the shutdown/logoff/etc buttons on it. It always appears if I wait a few minutes.

It can be annoying when you hit Ctrl-Alt-Delete to log on in a VMware session, though. ;)

---

