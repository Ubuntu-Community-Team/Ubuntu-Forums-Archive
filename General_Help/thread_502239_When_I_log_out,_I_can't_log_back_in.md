---
title: "When I log out, I can't log back in"
date: 2007-07-16
forum: General Help
---

### Post by James Hales on 2007-07-16
When I log out of Gnome, I can't log back in. After I've typed my user name and password, the login screen disappears and the screen turns blank - just to the background colour of GDM. About half of the time a white / gray box about the side of the gksudo dialog boxes appears in the top right hand side of the screen. The cursor appears and works as normal. No login sounds are heard.

One thing I have tried is changing the GDM settings from the Login Window Preferences dialog, so that X is restarted between sessions, however that made no effect. 

I switched over to a terminal once, after the blank screen appeared, to see what was going on. I ran "ps -aux" and found a bunch of processes running that appeared to be related to the Gnome startup, such as the gnome-keyring-daemon, gnome-settings-daemon, and a few aplay and gdmplay processes, trying to play some sounds (login.wav, question.wav).

I am not sure, but I don't think this has anything to do with GDM, but rather the process that starts up Gnome. I don't know anything about this process, or where any useful log files can be found, so I can't pin-point the problem.

Also, just so you know, I upgraded my system from a fresh install of Edgy to Feisty. Also I first noticed this problem while working on a custom GDM theme; as far as I can tell the theme hasn't got anything to do with it, because the problem comes up when using the default theme too.

Can anyone help me? Thanks for reading.

---

### Post by phidia on 2007-07-16
By any chance are you using/running compiz? Your problem sounds similar to some issues going on with gutsy right now and those (can't loging in-no desktop) are related or seem to be related to compiz.
You can try to open a tty/alternate shell by doing Alt+Ctrl+F1 and restarting gdm. > sudo /etc/init.d/gdm restart

---

### Post by James Hales on 2007-07-16
I am not running Compiz. Restarting GDM doesn't seem to work either, unfortunately.

Oh and I've tried completely emptying my home directory, in case any settings, etc. in there have been causing this, and that didn't work.

---

### Post by phidia on 2007-07-16
> **James Hales said:**
> I am not running Compiz. Restarting GDM doesn't seem to work either, unfortunately.

Oh and I've tried completely emptying my home directory, in case any settings, etc. in there have been causing this, and that didn't work.

Well we've ruled out/checked off a couple of possibilities then. Have you looked in /var/log (there's a lot of stuff there unfortunately) to see if there are any log files that might have a clue to this? I would look at dmesg, messages and any warning messages to start with. 

Are you able to get a alternate shell after this happens? I mean by that will Alt+Ctrl+F1 bring up the CLI?

---

### Post by stchman on 2007-07-16
> **James Hales said:**
> When I log out of Gnome, I can't log back in. After I've typed my user name and password, the login screen disappears and the screen turns blank - just to the background colour of GDM. About half of the time a white / gray box about the side of the gksudo dialog boxes appears in the top right hand side of the screen. The cursor appears and works as normal. No login sounds are heard.

One thing I have tried is changing the GDM settings from the Login Window Preferences dialog, so that X is restarted between sessions, however that made no effect. 

I switched over to a terminal once, after the blank screen appeared, to see what was going on. I ran "ps -aux" and found a bunch of processes running that appeared to be related to the Gnome startup, such as the gnome-keyring-daemon, gnome-settings-daemon, and a few aplay and gdmplay processes, trying to play some sounds (login.wav, question.wav).

I am not sure, but I don't think this has anything to do with GDM, but rather the process that starts up Gnome. I don't know anything about this process, or where any useful log files can be found, so I can't pin-point the problem.

Also, just so you know, I upgraded my system from a fresh install of Edgy to Feisty. Also I first noticed this problem while working on a custom GDM theme; as far as I can tell the theme hasn't got anything to do with it, because the problem comes up when using the default theme too.

Can anyone help me? Thanks for reading.

The same thing was happening on my laptop.  Whenever I restarted the workspace or logoff/logon I got a black screen.  It did not do it when I rebooted.  This cured it for me:

[http://www.stchman.com/feisty_tips.html](http://www.stchman.com/feisty_tips.html)

---

### Post by James Hales on 2007-07-17
@phidia

Yes, I can get an alternate shell. I've had a look at a lot of log files from /var/log/, such as dmesg, messages, syslog, Xorg.0.log, daemon.log and many others that just took my fancy. None of them seem to mention any fatal errors. 

From daemon.log, and another one I forgot, it looks as though the last thing mentioned before I log out or kill the X server each time is /etc/X11/Xsession. I looked around for an error log on that, and found .xsession-errors in my home directory.  The contents are as follows:

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "jameshales"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/jameshales:/tmp/.ICE-unix/5003

```

The same appears for a successful login, except with some notices about evolution and gnome-mount added to the end.

@stchman

Unfortunately that doesn't work for me. I think that method is pretty much equivalent to setting "Restart the X server with each login" in the Login Window Preferences dialog.

---

### Post by phidia on 2007-07-17
In re-reading your begining post here I was reminded that you upgraded to fiesty from edgy. How did you do that e.g with apt or synaptic and which method?
Sometimes a distribution upgrade will cause problems even though it shouldn't. If you are still having this problem you might want to try re-installing gnome and see if that changes things.

---

