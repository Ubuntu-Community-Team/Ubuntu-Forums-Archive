---
title: "Cron won't show notifications"
date: 2007-11-17
forum: General Help
---

### Post by blaster32 on 2007-11-17
Hi,

I'm currently trying to convince cron to display some notification information, but it just wont do it.
Neither notify-send nor zenity displays anything but everything is working fine if I execute the commands by hand.

Cron does run other commands, meaning it is running, it just wont let me know about it ;)

This is how my crontab looks like:
```

* * * * * DISPLAY=:0.0 zenity --info --title="title" --text="text"
* * * * * DISPLAY=:0.0 notify-send "title" "text"

```

Anyone got any ideas?

---

### Post by Brautigam on 2007-11-17
have you tried to restart the machine?

---

### Post by blaster32 on 2007-11-18
I'd be really surprised if that would be necessary.

No one else has any ideas? :(

---

### Post by blaster32 on 2007-11-20
I narrowed the problem to this:

```

libnotify-Message: Unable to get session bus: dbus-launch failed to autolaunch D-Bus session: Xlib: connection to ":0.0" refused by server

Xlib: No protocol specified


Autolaunch error: X11 initialization failed.

```

Still haven´t fixed it though. Any hints?

---

### Post by Pitxyoki on 2008-01-08
[QUOTE="Pitxyoki, about ten minutes ago"]Have you fixed this already?
I'm having the same problem...[/QUOTE]
[EDIT]Found the solution for me... I was missing a DISPLAY=:0.0

This is my crontab now:
```
$ crontab -l
# m h  dom mon dow   command
*/1 * * * * DISPLAY=:0.0 /usr/bin/notify-send Test "This is a test"
```
[/EDIT]

---

### Post by dcstar on 2008-01-08
> **blaster32 said:**
> Hi,

I'm currently trying to convince cron to display some notification information, but it just wont do it.
Neither notify-send nor zenity displays anything but everything is working fine if I execute the commands by hand.

Cron does run other commands, meaning it is running, it just wont let me know about it ;)

This is how my crontab looks like:
```

* * * * * DISPLAY=:0.0 zenity --info --title="title" --text="text"
* * * * * DISPLAY=:0.0 notify-send "title" "text"

```

Anyone got any ideas?

Cron runs in its own environment - not what you run in a terminal.

You should place explicit paths to all commands and not assume that because things work in a user terminal they will work in cron.

---

