---
title: "Run bash script (sudo) without showing terminal"
date: 2016-02-20
forum: General Help
---

### Post by senrabdet on 2016-02-20
Hi All:

I'm trying to figure out how to run a bash script that I need to run as sudo, and do so from a launcher or the apps menu.  Right now, I have to start the script in a terminal or have the terminal window pop open if I double click on it.  All in all,  I'm trying to emulate what happens when I launch something like iceweasel from the apps menu or a panel launcher where the app launches with a double click without using a a terminal window or having one show up.  

So far:

- I've adjusted the sudoers file with visudo adding "user ALL=(ALL) NOPASSWD: /bin/bash /usr/lib/script" and can run the script as a regular user if I launch it from a command prompt using "sudo bash /path/to/script".

- I've created a .desktop file in /usr/share/applications that calls the script from /usr/lib but so far it only seems to work if I include mate-terminal -e "/path/to/script" which again opens a terminal window

- I've tried compiling the script using shc, added a path variable to .bashrc and can launch the complied script from a command prompt, but not if I add the same command to a launcher

- tried various commands in a launcher, but the only ones that work include "mate-terminal -e" which opens a terminal window

My guess is this has something to do with my not understanding what's going on with commands issued in terminals vs. scripts or launchers, and how in the former the command may actually be being passed between sessions?  I also assume this is something for those with deeper knowledge is not a big deal...but it is completely stumping me.

Q:  can anyone suggest how to accomplish this, where I can use a launcher on my panel or from the app menu, launch a script that requires sudo for a regular user, and not have the terminal window pop up?  Thanks!

---

### Post by sudodus on 2016-02-20
You can see how I'm doing it or at least something similar with mkusb.

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

mkusb is a bash shellscript, and it is started from a desktop file via a starter script. There are probably easier ways to do it, but I want to run mkusb two ways

1 - started from a desktop file and writing the 'console output' to a log file

2 - started from a terminal window with possible parameters and writing to the terminal window.

---

### Post by ik-0 on 2016-02-20
sudo requires a tty by default even with nopasswd.
see the following as a workaround [http://serverfault.com/questions/246135/is-it-possible-to-use-sudo-with-requiretty-for-a-specific-command](http://serverfault.com/questions/246135/is-it-possible-to-use-sudo-with-requiretty-for-a-specific-command)

---

### Post by senrabdet on 2016-02-20
Thanks so much!  Will check out both suggestions, report back.  Appreciate it!

---

### Post by senrabdet on 2016-02-22
Hi All - quick update.  Have not gotten either solution to work yet, so for now am going with "kludge" of " & sleep .5 && kill `pidof mate-terminal` " (without quotes).  May revisit, but regardless, really appreciate the help!

---

### Post by ian-weisser on 2016-02-22
Running root-level proceses as a normal user is rarely a good idea.

The way most Ubuntu developers solve the problem is to run two processes, one root-level and one user-level. The two usually communicate using dbus.

Examples: Network Manager and Power Manager work this way.

---

### Post by ik-0 on 2016-02-23
post your sudoers files. I've gotten this to work on a couple of occasions using no tty.

---

### Post by HermanAB on 2016-02-23
You can use gksu or kdesu.

---

