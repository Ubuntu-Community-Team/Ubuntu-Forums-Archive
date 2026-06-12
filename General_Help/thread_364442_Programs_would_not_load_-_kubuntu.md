---
title: "Programs would not load - kubuntu"
date: 2007-02-18
forum: General Help
---

### Post by yurukov on 2007-02-18
Sometimes when I start a program it would not open up. I see the jumping icon that comes in KDE, but then no window opens up. That has happened mostly with the update manager, Firefox and the system settings. The process is also finished - I see it for a time in "top", but is just finished before any window has opened and the jumping icon goes away. Any idea?

---

### Post by nereid on 2007-02-18
Sorry but no, I've got the same problem from time to time. Mostly with adept. Another reason why I use the command line ;)

---

### Post by yurukov on 2007-02-18
Yeah, come to think of it - it never happened from the command line. I open a shell each time a program would not open 2 times in a row. :KS

---

### Post by Detonate on 2007-02-18
What causes this, is KDE remembers the last time you opened the program and tries to open it the same way.  This does not always work.

The solution is to add the following line to the /etc/sudoers file in the "Defaults" section.

Defaults	timestamp_timeout=0

Be very careful editing this file, because if you make a mistake, it will lock out your sudo privileges and you will have to reboot in recovery mode and edit the file with VI from the recovery command line to fix it.  Don't ask me how I know.:) 


This is what my Kubuntu /etc/sudoers file looks like.

[B][I]# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn
Defaults	timestamp_timeout=0
# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL[/I][/B]


Floyd

---

### Post by yurukov on 2007-02-18
Thanks, I will see if I get any more problems.

---

### Post by yurukov on 2007-02-19
Thanks, that solved the problem.

---

