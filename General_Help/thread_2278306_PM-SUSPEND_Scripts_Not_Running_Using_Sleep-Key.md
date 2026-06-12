---
title: "PM-SUSPEND Scripts Not Running Using Sleep-Key"
date: 2015-05-15
forum: General Help
---

### Post by naroyce on 2015-05-15
I'm finding that the scripts under "/etc/pm/sleep.d" don't seem to run unless "pm-suspend" is manually invoked.

If I press the "Sleep" key on my keyboard, or if I click the "Suspend" menu item under the power cog, the scripts don't seem to run.
I have a test item meant to fix my audio issue, but when it didn't work, I added a "logger" statement and that didn't even show in the logs. I then added "touch" statements and the files were never touched.
```
$ sudo gedit /etc/pm/sleep.d/50alsa
```
```

#!/bin/bash# Restore audio
touch /home/nater/Desktop/test1
logger test1
logger $1
case "$1" in
     hibernate|suspend)
touch /home/nater/Desktop/test2
             # Stopping is not required
             ;;
     thaw|resume)
touch /home/nater/Desktop/test3
logger test2
             /usr/bin/pulseaudio -k && sudo /sbin/alsa force-reload
logger test3
touch /home/nater/Desktop/test4
             ;;
     *) exit $NA
             ;;
esac
```
```
$ sudo chmod +x /etc/pm/sleep.d/50alsa
```
**Works** (files touched, log written to):
 manually invoke: "$ sudo pm-suspend"
**Does Not Work** (files NOT touched, log NOT written to):
 Press "Sleep" key on keyboard.
 Click "Suspend" menu item under power cog.

Bug?

---

### Post by dino99 on 2015-05-15
if you are using vivid then systemd is the default. Maybe that script needs a fix to be compatible with it. In that vivid case, switch to upstart when booting to see if the script works then.

---

### Post by tgalati4 on 2015-05-16
Open a terminal and run *xev*.  Place the mouse cursor in the box and type the sleep key and see if there is a valid keycode associated with it.  If so, then perhaps assign *pm-suspend* command to it.  You may have to work on permissions, since keyboard shortcuts are run with user privilege.

---

### Post by matt_symes on 2015-05-16
Hi

systemd does not use pm-utils. 

This is why your scripts are not invoked when you sleep using the sleep key but are invoked using a call to one of the pm-utils commands directly.

You'll need to create to create a service file for the suspend and hibernate targets.

There is a pretty good write-up on the Arch wiki.

Kind regards

---

