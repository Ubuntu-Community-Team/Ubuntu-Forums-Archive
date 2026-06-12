---
title: "Xubuntu: How to lock screen automatically on hibernate?"
date: 2007-07-06
forum: General Help
---

### Post by UJoe4 on 2007-07-06
Both KDE and GNOME automatically lock the session/screen on hibernation (prior to calling /etc/acpi/hibernate.sh), so that you have to enter your password when you resume.

But Xfce doesn't: It just hibernates, so when you resume it goes straight back to your session without a login screen. Is there any way to change this? I haven't found an option in the Settings menu. How would you lock the screen/session from the command line (so I could put it in a script)?

Under Settings > Screensaver it shows that XScreenSaver is enabled, and I can lock the screen manually by pressing Ctrl-Alt-Del, but I can't figure out how to do it automatically or from the command line.

Thanks.

---

### Post by UJoe4 on 2007-07-06
OK, turns out that to replicate the Ctrl-Alt-Del behavior (XScreenSaver locking the screen) you run:
> xscreensaver-command -lock
The problem is that putting this in my /etc/acpi/hibernate.sh script doesn't work, I think because whoever "runs" hibernate.sh when the computer hibernates (root?) somehow doesn't have permission to access the graphical interface. 

Trying "xscreensaver-command -lock" from a shell works when I'm my regular user. But from a root shell it doesn't, and I get this error message:
> Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xscreensaver-command: can't open display :0.0
(And prefacing it with sudo -u myregularusername doesn't work either.) I thought I had solved this problem when, because of a different issue, I had to add:
> ,env_reset,env_keep+="DISPLAY HOME XAUTHORIZATION"
to the end of the Defaults line of my /etc/sudoers file, but I guess not. (Taking it out and putting it back in doesn't make a difference for the xscreensaver problem.)

I really don't understand any of this display authorization stuff, could somebody help out? I just want to be able to add that xscreensaver line to my hibernate.sh script, or else find another way to have the screen locked when resuming from hibernation.

---

### Post by UJoe4 on 2007-07-08
Turns out I needed to use "su myregularusername" instead of "sudo -u myregularusername". So just add this to the beginning of /etc/acpi/hibernate.sh:
> if ps -e|grep xfdesktop
then
su [myregularusername] xflock4
fi
Then every time the system hibernates, it will check whether Xfce is running and if so, lock the screen with XScreenSaver. Then you'll need a password to resume. I'm not sure why this isn't the default behavior out of the box (it is in GNOME and KDE).

A different solution is that if XScreenSaver is enabled during your regular session (say, set to lock the screen after 30 minutes of inactivity), it will ask for a password if you resume more than 30 minutes after you hibernated but not otherwise. But that's not nearly as good since it doesn't work for shorter hibernation periods, and you need to have XScreenSaver enabled during your regular session for it to work at all.

---

### Post by knyar on 2007-12-23
> **UJoe4 said:**
> Turns out I needed to use "su myregularusername" instead of "sudo -u myregularusername". So just add this to the beginning of /etc/acpi/hibernate.sh:


Apparently this did not work on my Xubuntu 7.10. So I modified it a bit:
> 
if /bin/ps -e | /bin/grep xfdesktop
then
        LOGIN=`/bin/grep $HAL_METHOD_INVOKED_BY_UID /etc/passwd | /usr/bin/cut -f 1 -d :`
        pids=`/usr/bin/pgrep -u $LOGIN xfce4-session`
        for pid in $pids; do
          DBUS_SESSION_BUS_ADDRESS=`/bin/grep -z DBUS_SESSION_BUS_ADDRESS /proc/$pid/environ | /bin/sed -e 's/DBUS_SESSION_BUS_ADDRESS=//'`
          DBUS_SESSION_BUS_ADDRESS=$DBUS_SESSION_BUS_ADDRESS /bin/su $LOGIN /usr/bin/xflock4
        done
fi


(it also detects your username automatically)

---

### Post by michabbs on 2008-04-20
Knyar's solution did not work for me, so I made it so:

```
for PID in `/usr/bin/pgrep xfdesktop`; do
  DBUS_SESSION_BUS_ADDRESS=`(/bin/cat /proc/$PID/environ; /bin/echo)|/usr/bin/tr "\000" "\n"|/bin/grep DBUS_SESSION_BUS_ADDRESS|/bin/sed -e 's/DBUS_SESSION_BUS_ADDRESS=//'`
  LOGIN=`/bin/ps -ouser -p $PID --no-headers`
  DBUS_SESSION_BUS_ADDRESS=$DBUS_SESSION_BUS_ADDRESS /bin/su $LOGIN /usr/bin/xflock4
done

```

It detects user names and lock all open sessions.

---

