---
title: "gnome terminal abort"
date: 2017-01-31
forum: General Help
---

### Post by knight69 on 2017-01-31
I recently upgraded from ubuntu 14.04 to 16.04 and everything appeared to go without a hitch.  After testing numerous applications, all of which appeared to work perfectly, I went to open the gnome terminal.  For a short moment there was a message "starting terminal" at the bottom, but then nothing happened. A review of syslog showed the following: 

```

Jan 31 13:48:01 I-5 gnome-session[2508]: (process:2951): Gtk-WARNING **: Locale not supported by C library.
Jan 31 13:48:01 I-5 gnome-session[2508]: #011Using the fallback 'C' locale.
Jan 31 13:48:09 I-5 gnome-session[2508]: (process:2971): Gtk-WARNING **: Locale not supported by C library.
Jan 31 13:48:09 I-5 gnome-session[2508]: #011Using the fallback 'C' locale.
Jan 31 13:48:09 I-5 org.gnome.Terminal[2383]: Locale not supported.
Jan 31 13:48:09 I-5 gnome-session[2508]: Error constructing proxy for org.gnome.Terminal:/org/gnome/Terminal/Factory0: Error calling StartServiceByName for org.gnome.Terminal: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process org.gnome.Terminal exited with status 9
```

wiki.gnome.org give the reason for this as:

[I]Reason: The locale settings in the environment that gnome-terminal-server is started with describe a nonexistent locale.

[/I]I have uninstalled and reinstalled gnome-terminal.  I have removed, reinstalled and reconfigured locales.  I have ensured that all my locale settings are set to en_US.UTF-8. and can find no instance where there is a non-existent locale (whatever that means).

Any help resolving this issue will be greatly appreciated.:o

PS  Sorry, I can't figure out how to get rid of these icons.

---

### Post by Perfect Storm on 2017-01-31
> PS Sorry, I can't figure out how to get rid of these icons.

fixed.

---

### Post by knight69 on 2017-01-31
Problem soved.  Added the following line to the bottom of the list in /etc/default/locale

LC_ALL="en_US.UTF-8"

and after re-booting the gnome terminal opened right up.

---

