---
title: "Running a shell session script in the background"
date: 2007-07-06
forum: General Help
---

### Post by Danie.Brink on 2007-07-06
Hi,

I really hope someone can help - with this, I've spent almost a week trying to get this silly thing going but it just won't.

I'm trying to run a script that will clean up unessecary processes whenever the screensaver activates.  The solution I have (now split into 3 scripts to try & help debugging) runs a process for dbus-monitor to execute the cleanup script when the screensaver activates. This part works. The problem is that when I add the init script to the startup applications (under preferences-> Sessions) to get the 'service' running the login just hangs - looks like the init script is not returning control back after setting off the service process. The 2 scripts (init script & service script) are below:

cleansessionservice_init.sh (the script that's supposed to start the service up in the background):

> #!/bin/sh

/usr/bin/perl /usr/bin/cleansessionservice.pl &



And cleansessionservice.pl (the 'service' that should keep running):

> #!/usr/bin/perl -w

my $cmd = "dbus-monitor --session \"type='signal',interface='org.gnome.ScreenSaver',member='SessionIdleChanged'\"";

open (IN, "$cmd |");

while (<IN>) {
    if (m/^\s+boolean true/) { system ('/usr/bin/cleansession.pl') };
}


If I run the 1st one (cleansessionservice_init.sh) in a terminal it starts the service up fine & returns straight away, but when I add it to the startup programs the session just hangs.

Anyone have some help for someone who'se obviously missing something really stuupid?

---

### Post by CheShA on 2007-08-20
I managed to get something similar runningn - check out [this thread]("http://ubuntuforums.org/showthread.php?t=368755&highlight=screensaver+script")

---

