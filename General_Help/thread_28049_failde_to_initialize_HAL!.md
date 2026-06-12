---
title: "failde to initialize HAL!"
date: 2005-04-18
forum: General Help
---

### Post by juliocesargarcia on 2005-04-18
I have a couple of problems that I think are related:

When I start GNOME, I get the error

failed to initialize HAL!

and when I boot, I see an error to the effect that the dbus-1 startup script gets a segmentation violation.

I found this link and reinstalled according to the suggestions there:

[http://www.ubuntuforums.org/showthread.php?t=24146](http://www.ubuntuforums.org/showthread.php?t=24146)

The problem persists. I had no problems with this system and 4.10 for months. 5.04 is causing the problem.

---

### Post by diebels on 2005-04-18
Maybe something is screwed up with dbus-1 too. You could try:
sudo apt-get install --reinstall dbus-1

---

### Post by juliocesargarcia on 2005-04-19
Just did that. It still fails. Here is the output:

~ > sudo /etc/init.d/dbus-1 stop
 * Stopping Hardware abstraction layer:                                  [ ok ]
 * Stopping system message bus:                                          [ ok ]
~ > sudo /etc/init.d/dbus-1 start
 * Starting system message bus:
/etc/init.d/dbus-1: line 30: 24396 Segmentation fault      start-stop-daemon --start --quiet --pidfile $PIDFILE --user $DAEMONUSER --exec $DAEMON -- --system $PARAMS

---

### Post by Soylent on 2005-04-19
I still have the same problem hope someone will find the solution 

bye all

---

### Post by julius malchovitch on 2005-04-19
[QUOTE=Soylent]I still have the same problem hope someone will find the solution 

bye all[/QUOTE]

I had the same behaviour after editing /etc/hdparm.conf to enable DMA on my dvd drives (it was disabled by default)

If you don't have problems with DMA enabled by default you can try to comment out all the lines in /etc/hdparm.conf or remove hdparm from init scripts.

Bye

---

### Post by juliocesargarcia on 2005-04-20
No luck :-( I had not edited hdparm.conf (by default all that was in it was "quiet"), but I booted with nohdparm and I got the same problem.

---

### Post by diebels on 2005-04-20
So something failes at line 30 or in the block that starts at line 30 in this script(line 46 i guess):
```
#! /bin/sh
# -*- coding: utf-8 -*-
# Debian init.d script for D-BUS
# Copyright © 2003 Colin Walters <walters@debian.org>

set -e

DAEMON=/usr/bin/dbus-daemon-1
NAME=dbus-1
DAEMONUSER=messagebus
PIDDIR=/var/run/dbus
PIDFILE=$PIDDIR/pid
DESC="system message bus"
EVENTDIR=/etc/dbus-1/event.d

test -x $DAEMON || exit 0

. /lib/lsb/init-functions

# Source defaults file; edit that file to configure this script.
ENABLED=1
PARAMS=""
if [ -e /etc/default/dbus-1 ]; then
  . /etc/default/dbus-1
fi

test "$ENABLED" != "0" || exit 0

start_it_up()
{
  if [ ! -d $PIDDIR ]; then
    mkdir -p $PIDDIR
    chown $DAEMONUSER $PIDDIR
    chgrp $DAEMONUSER $PIDDIR
  fi
  if [ -e $PIDFILE ]; then
    PIDDIR=/proc/$(cat $PIDFILE)
    if [ -d ${PIDDIR} -a  "$(readlink -f ${PIDDIR}/exe)" = "${DAEMON}" ]; then 
      log_success_msg "$DESC already started; not starting."
    else
      log_success_msg "Removing stale PID file $PIDFILE."
      rm -f $PIDFILE
    fi
  fi
  log_begin_msg "Starting $DESC: "
  start-stop-daemon --start --quiet --pidfile $PIDFILE \
    --user $DAEMONUSER --exec $DAEMON -- --system $PARAMS
  log_end_msg $?
  if [ -d $EVENTDIR ]; then
      run-parts --arg=start $EVENTDIR
  fi
}

shut_it_down()
{
  if [ -d $EVENTDIR ]; then
      run-parts --reverse --arg=stop $EVENTDIR
  fi
  log_begin_msg "Stopping $DESC: "
  start-stop-daemon --stop --retry 60 --quiet --oknodo --pidfile $PIDFILE \
    --user $DAEMONUSER
  # We no longer include these arguments so that start-stop-daemon
  # can do its job even given that we may have been upgraded.
  # We rely on the pidfile being sanely managed
  # --exec $DAEMON -- --system $PARAMS
  ES=$?
  log_end_msg $ES
  rm -f $PIDFILE
}

case "$1" in
  start)
    start_it_up
  ;;
  stop)
    shut_it_down
  ;;
  restart|force-reload)
    shut_it_down
    sleep 1
    start_it_up
  ;;
  *)
    log_success_msg "Usage: /etc/init.d/$NAME {start|stop|restart|force-reload}" >&2
    exit 1
  ;;
esac

exit 0
```
Not sure what's causing this on your system. Funny hardware, file corruption, bad configuration somewhere? Try to see what it does to locate the problem. Check content and ownership of /var/run/dbus/, look for info in logfiles, unplug unessential hardware, and so on. Maybe open a bug for it.

---

### Post by julius malchovitch on 2005-04-21
I'd like to reassume my experience with dma/hal on hoary.
After installing the distro I noticed DMA was disabled by default on my cdrom drives. The most natural thing to do was to edit hdparm.conf to enable dma on the proper drives. After rebooting the system I noticed on console that the system was hanging at "setting disc parameters" and trying to login in gnome ended up in the well known "failed to initialize hal".
I moved hdparm from S07 to S99 as suggested somewhere on these forums but I still had the same issue.

I also noticed that **removing** hdparm from startup runlevels but leaving hdparm.conf uncommented did not help, so I guess hdparm.conf is parsed by some other startup script I am not aware of.

Even manually putting hdparm -d1 /dev/hdc (hdc is my dvd drive) in .bashrc and commenting out every line in hdparm.conf caused the "failed to initialize HAL!" problem when logging in gnome (this solution may work if logging in from a terminal, because gnome-volume-manager is not loaded).

To enable DMA on gnome login I finally decided to adopt this solution (well, it's not a solution, it's a workaround), put the following script in your path and make it executable:
```

#!/bin/sh
# start_dma.sh
sleep 10
sudo /sbin/hdparm -d1 /dev/hdc
sudo /sbin/hdparm -d1 /dev/hdc

```

then in gnome open the session properties dialog (System -> Preferences -> Session), in the "startup programs" tab (the names may be different, I am not using  english i18n) add a new entry, browse to the path you put the above script, and put 90 in the number field.

Note that removing the "sleep 10" line from the above script could lead to a "failed to initialize hal"  problem because the hdparm command in the script could run before gnome-volume-manager startup.

Hope this solution will work for all those experiencing the same problem

Best, 
Luca

EDIT: The above script to work properly needs the following lines to be added in /ets/sudoers:
```

Cmnd_Alias HDPARM=/sbin/hdparm
%admin  ALL=(ALL) NOPASSWD:     HDPARM

```

---

### Post by juliocesargarcia on 2005-05-05
[QUOTE=juliocesargarcia]I have a couple of problems that I think are related:

When I start GNOME, I get the error

failed to initialize HAL!

and when I boot, I see an error to the effect that the dbus-1 startup script gets a segmentation violation.

I found this link and reinstalled according to the suggestions there:

[http://www.ubuntuforums.org/showthread.php?t=24146](http://www.ubuntuforums.org/showthread.php?t=24146)

The problem persists. I had no problems with this system and 4.10 for months. 5.04 is causing the problem.[/QUOTE]
 Well, I see that others are having this problem. FWIW, I'm guessing I still have this problem, but my GNOME desktop started working as if by magic. I came in this morning after being away for 6 days and things are working. It is almost as if it took a week to run through a pile of timeouts and it now works. Strange. I will not logout for the forseeable future :-)

---

### Post by bjunix on 2005-05-05
Its the same problem here. i didnt changed any of my configuration. the problem came out of nothing.

---

### Post by Gandalf on 2005-05-05
i had the same problem when i uninstalled KDE, my solution was simple
sudo apt-get install --reinstall acpi acpi-support acpid

my problem was the acpid not starting i did reinstall only acpid but no harm to reinstall the three of them just in case tell me if it worked

---

### Post by pseudonym on 2005-05-28
[QUOTE=julius malchovitch]To enable DMA on gnome login I finally decided to adopt this solution (well, it's not a solution, it's a workaround), put the following script in your path and make it executable:
```

#!/bin/sh
# start_dma.sh
sleep 10
sudo /sbin/hdparm -d1 /dev/hdc
sudo /sbin/hdparm -d1 /dev/hdc

```
then in gnome open the session properties dialog (System -> Preferences -> Session), in the "startup programs" tab (the names may be different, I am not using  english i18n) add a new entry, browse to the path you put the above script, and put 90 in the number field.

Note that removing the "sleep 10" line from the above script could lead to a "failed to initialize hal"  problem because the hdparm command in the script could run before gnome-volume-manager startup.

Hope this solution will work for all those experiencing the same problem

Best, 
Luca

EDIT: The above script to work properly needs the following lines to be added in /ets/sudoers:
```

Cmnd_Alias HDPARM=/sbin/hdparm
%admin  ALL=(ALL) NOPASSWD:     HDPARM

```[/QUOTE]

Thanks, but I tried this and it's not working. I commented out everything in /etc/hdparm.conf and, because I have two ide optical drives (CD-RW, DVD-+RW) my shell script looks like this -

```

#!/bin/sh
# start_dma.sh
sleep 10
sudo /sbin/hdparm -d1 /dev/hdc
sudo /sbin/hdparm -d1 /dev/hdc
sudo /sbin/hdparm -d1 /dev/hdd
sudo /sbin/hdparm -d1 /dev/hdd

```

Thinking the duplicated lines looked slightly odd, I also tried it with just one line for each device. I placed the script in /usr/sbin, added it to gnome startup, and edited /etc/sudoers like you wrote, but dma still doesn't get turned on. I haven't noticed any error messages in any of the log files, either.

Do you have any idea as to what might stop this from working?

I guess the good news is that the 'failed to initialize HAL' problem disappears if you don't try to turn DMA on at startup. It's not a huge problem either, especially as I don't use either drive that often. When I do, I just run sudo hdparm -d1 /dev/hd*. Still, this is one of an increasingly long list of steps/commands I need to remember to carry out just to get simple things working the way I want, and which you shouldn't normally have to worry about. :(

---

### Post by benplaut on 2005-05-28
nobody caught this?!?!

2001 Space Odysee  \\:D/ 

"*I'm sorry Dave, I'm afraid I can't do that*"

(got that set as my system error message  :roll: )

---

### Post by pseudonym on 2005-05-28
It's the developer's nod to Stanley Kubrick.

lol I love Ubuntu, but sometimes this computer does seem like it's behaving like HAL from 2001! :)

---

