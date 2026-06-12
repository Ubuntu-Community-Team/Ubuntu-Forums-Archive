---
title: "Starting Calendar Server on boot"
date: 2007-12-28
forum: General Help
---

### Post by poonaka on 2007-12-28
I instead Calendar Server: [http://trac.calendarserver.org/projects/calendarserver](http://trac.calendarserver.org/projects/calendarserver) following instructions from here: [http://cam.moobox.org/blog/?p=5](http://cam.moobox.org/blog/?p=5) and I can use it by running:

/usr/local/CalendarServer/run

I'd like to have it start up on boot but have no clue how :(

---

### Post by arvevans on 2007-12-28
You didn't say which window manager you were running, so I'm going to assume "Gnome":
Go to ***System.Preferences.Sessions*** and add your command line as a new entry.  This should start it at boot time.

Arv
_._

---

### Post by poonaka on 2007-12-28
sorry forgot to mention that I'm not using a GUI.  I'm running the server version of gutsy.

---

### Post by arvevans on 2007-12-28
OK.  This is still possible, just a little more risky, because we now need to play with initialization files without benefit of a GUI to keep us honest.

In Linux (and in all UNIX/POSIX derivatives) system initialization is controlled by a set of initialization tables, usually called "rc files".  These are located in /etc/rc0.d through /etc/rc6.d, with rc5.d being normal run level for user support.  You can start by taking a look in /etc/rc5.d to see what is called when your system completes booting and starts all the user support functions.

There is also a directory at /etc/init.d which contains scripts for starting a number of  functions that need code to help them self-configure at start time.

Let me insert the usual disclaimer here:
[INDENT]**_Mucking around in rc files or init files may break your operating system.  You need to do the research to make sure you know what you are doing before changing things here.  If your system has critical data stored on it, you should back that data up to a CD, DVD, or other safe storage & recovery medium before doing anything with rc or init files._**[/INDENT]

Arv
_._

---

