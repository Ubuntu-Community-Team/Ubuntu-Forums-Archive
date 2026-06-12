---
title: "crontab + rhythmbox = NO JOY  :("
date: 2007-09-26
forum: General Help
---

### Post by radnor on 2007-09-26
Hello all!

I want to control rhythmbox VIA crontab and so far cannot...

I've used the following commands in crontab -e:
01,02 * * * * rhythmbox-client --play-pause
01,02 * * * * DISPLAY-:0 && rhythmbox-client --play-pause
01,02 * * * * DISPLAY-:0.0 && rhythmbox-client --play-pause

I've added /usr/bin/ in front of the rhythmbox command still without any luck

I looked at the syslog and can see the editing, saving, restarting and execution of the command but it does not toggle the status of rhythmbox..

TIA for the help!

Radnor

---

### Post by pointone on 2007-09-26
You should specify the user you want to run the commands as: in this case, yourself.

EDIT: Whoops! Sorry, didn't see you were using crontab -e. Disregard this post! :P

---

### Post by radnor on 2007-09-26
Not a problem.... I'd use CRON if it would work.  (Tried it, but not as many options as I tried using CRONTAB)

---

### Post by jimoz on 2008-04-04
See post [http://ubuntuforums.org/showthread.php?t=438639](http://ubuntuforums.org/showthread.php?t=438639)

Finally got it working well! After I saw that thread, it wasn't too hard. I have cron set up to run:

30 8 * * * export DBUS_SESSION_BUS_ADDRESS=$(/pathto/rbadd.sh) && rhythmbox-client --play-pause

Where rbadd.sh returns the dbus address variable, which would otherwise change every time its reloaded.

rbadd.sh:

#!/bin/bash

rb_pid=$(pgrep -u usernamehere -o rhythmbox)
input_text=$(</proc/$rb_pid/environ)
strip_beg=${input_text##*DBUS_SESSION_BUS_ADDRESS=}
dbus_ass=${strip_beg%%GNOME*}
echo $dbus_***

I'm pretty new to linux scripting so its probably a very ugly way of doing it, but hey - it works for me.

---

### Post by hwttdz on 2008-07-18
export DISPLAY=:0 && rhythmbox-client && sleep 3 && rhythmbox-client --play

What I use, I don't know if starting rhythmbox then waiting for it to open before starting it playing is entirely necessary, but it works for me.  This seemed a little simpler than the previous solution (plus I couldn't get that to work).  Sorry if I'm really waking a dead thread, google brought me here.

---

### Post by Joeb454 on 2008-10-03
[Hemebond]("http://ubuntuforums.org/member.php?u=5702") on the forums PM'd me with a solution to this thread, so I added it.

It's a script that you run with cron, please find it below :)

```
#!/bin/bash
# This script will start Rhythmbox properly so that media keys and other cron
# jobs can still access it. Save as anything but "rhythmbox".

# Save as a script. Make it executable. Call the script, via Cron, with
# whatever regular rhythmbox-client option you want to e.g., --play, --pause

# Get the PID for existing Rhythmbox process.
PID=$(pgrep -u $LOGNAME -o -x rhythmbox)

# Rhythmbox is not running. Get PID of other DBUS process.
if [ -n $PID ] ; then
	PID=$(pgrep -u $LOGNAME -o -x notification-da)
fi

# Find DBUS session bus for this session and export it.
DBUS_SESSION_BUS_ADDRESS=`grep -z DBUS_SESSION_BUS_ADDRESS /proc/$PID/environ 2>/dev/null`
export $DBUS_SESSION_BUS_ADDRESS

# Start Rhythmbox.
/usr/bin/rhythmbox-client --no-present

# Wait for Rhythmbox to finish loading. Adjust if necessary.
sleep 3

# Tell Rhythmbox to start playing.
/usr/bin/rhythmbox-client $1
```

Any questions should be directed to Hemebond

---

