---
title: "xfce4-session-logout and power button doesn't bring up a logout confirmation screen"
date: 2014-06-28
forum: General Help
---

### Post by theway645 on 2014-06-28
xfce4-session-logout and power button doesn't bring up a logout confirmation screen, it just logs out the pc without any kind of confirmation what so ever. I've been having this problem for sometimes now. Has anyone experianced this bug ? please help it is getting on my nerves. I will send 5 mbtc for the best or fastest anwer that works.

---

### Post by ajgreeny on 2014-06-28
Have a look in the General tab of the xfce  Power Manager, which you may only be able to get to from the settings-manager.

You should be able to set the "When Power button is pressed" to "Ask" not "Shutdown", which is what I suspect is showing at the moment.
If that does not work I do not know what else to suggest.

---

### Post by theway645 on 2014-06-28
Thanks for the reply but the power button is set to Ask and not Shutdown. I think that it is some kind of bug but have no idea how to fix it.

---

### Post by Toz on 2014-06-28
Is it possible that xfce4-session is crashing and dumping you out before the normal shutdown routines start? If so, you would notice that Xfce quits rather abruptly. There might also be some log entries in ~/.xsession-errors (and ~/.cache/upstart/startxfce4.log if you're using 14.04) and possibly also /var/log/Xorg.0.log.

---

### Post by theway645 on 2014-06-28
It might very well be that but the problem is that I have not idea how to fix the bug.

---

### Post by Toz on 2014-06-28
Maybe you can post back those log files so that we can have a look? Use pastebinit like this:
```
pastebinit ~/.xsession-errors
```
```
pastebinit ~/.xsession-errors.old
```
```
pastebinit ~/.cache/upstart/startxfce4.log
```
```
pastebinit /var/log/Xorg.0.log
```
...and post back the links that are generated.

If there are any error messages in those log files related to xfce4-session, we can research them to see if it is a bug and/or if a fix exists.

---

### Post by theway645 on 2014-06-28
Here are the links

pastebinit ~/.xsession-errors = [http://paste.ubuntu.com/7718073/](http://paste.ubuntu.com/7718073/)

pastebinit ~/.xsession-errors.old = [http://paste.ubuntu.com/7718080/](http://paste.ubuntu.com/7718080/)

pastebinit ~/.cache/upstart/startxfce4.log = [http://paste.ubuntu.com/7718085/](http://paste.ubuntu.com/7718085/)

pastebinit /var/log/Xorg.0.log = [URL="http://paste.ubuntu.com/7718088/"]http://paste.ubuntu.com/7718088/

[/URL]

---

### Post by Toz on 2014-06-28
Can you also post back /var/log/Xorg.0.log.old?

And also, the results of:
```
zcat ~/.cache/upstart/startxfce4.log.1.gz | grep -A5 xfce4-session
```

---

### Post by theway645 on 2014-06-29
The output of 
```
zcat ~/.cache/upstart/startxfce4.log.1.gz | grep -A5 xfce4-session
```

```
(xfce4-session:1925): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
/usr/bin/startxfce4: X server already running on display :0
xfce4-session: GNOME compatibility is enabled and gnome-keyring-daemon is found on the system. Skipping gpg/ssh-agent startup.
[1404022818] [ERR] hddtemp: failed to open connection.
[1404022818] [ERR] Failed to retrieve NVIDIA information.
[Info  08:20:18.849] Docky version: 2.2.0 Release
[Info  08:20:18.970] Kernel version: 3.13.0.30
```

---

### Post by Toz on 2014-06-29
Nothing there. How about /var/log/Xorg.0.log.old:
```
pastebinit /var/log/Xorg.0.log.old
```

Do you autostart steam on your system? Have you tried shutting down without steam running, or not having run steam at all for that session?

---

### Post by theway645 on 2014-06-29
I have just tried but there is no change : (

---

### Post by Toz on 2014-06-29
What does the following return?
```
xfce4-power-manager --dump
```

---

