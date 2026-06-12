---
title: "Serious operating system problems"
date: 2012-11-10
forum: General Help
---

### Post by Jacob72 on 2012-11-10
Hello,

I am having serious problems with my operating system, Xubuntu 12.04. Software programs/folders do not open properly, they do not expand (firefox crashes when I try to make window full size), I can not navigate through open applications using tab, applications do not respond. Right click on the mouse brings up the options box but it does not stay visible when I try to select an option ... 

Task Manager shows I am only using %15 memory and 7% CPU and I have plenty of HD space, I have never experienced anything like this before running X/Ubuntu.

I recently installed xubuntu desktop environment all was running fine for a week or so. I have downloaded a website via ftp for uploading on to a new server - virus?

Thanks for any help

Probable an absentminded user fault - still loving Ubuntu :)

---

### Post by Toz on 2012-11-10
Sounds like you might have a corrupted session. Try logging out, going to your first console (Ctrl+Alt+F1), logging in to the text console and running these commands:
```

cd ~/.cache
rm -rf sessions

```
...then go back to your gui console (Ctrl+Alt+F7) and log back in.

These commands will clear the existing saved sessions state and hopefully fix your problems. If not, please post back the contents of ~/.xsession-errors:
```
pastebinit ~/.xsessions-errors
```
...and post back the lin kthat is generated.

---

### Post by Jacob72 on 2012-11-11
Hello Toz,

Thanks once again, that seemed to clear everything up :)

Would be interested to know what caused the corrupted sessions?

This command
```

pastebinit ~/.xsessions-errors

```

Only produced this?
Unable to read from: /home/jacob/.xsessions-errors

Jacob

---

### Post by Toz on 2012-11-11
> Unable to read from: /home/jacob/.xsessions-errors
Does the file exist (it should):
```
ls -l ~/.xsession-errors
```

---

### Post by Jacob72 on 2012-11-13
> **Toz said:**
> Does the file exist (it should):
```
ls -l ~/.xsession-errors
```

Yes, that code command produced; /home/jacob/.xsessions-errors

I logged in just now and I was back to the corrupted sessions state? I am OK for now as I followed the steps as before, the last command still produces this:

```

jacob@jacob-desktop:~$ pastebinit ~/.xsessions-errors
Unable to read from: /home/jacob/.xsessions-errors
```

---

### Post by Toz on 2012-11-13
Can you view the file using leafpad?
```
leafpad ~/.xsession-errors
```

---

### Post by Jacob72 on 2012-11-13
> **Toz said:**
> Can you view the file using leafpad?
```
leafpad ~/.xsession-errors
```

openConnection: connect: No such file or directory
cannot connect to brltty at :0
xrdb:  "Xft.hinting" on line 13 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 14 overrides entry on line 7
xfce4-settings-helper: Another instance is already running. Leaving...

(polkit-gnome-authentication-agent-1:2782): GLib-CRITICAL **: g_variant_new_string: assertion `string != NULL' failed

(polkit-gnome-authentication-agent-1:2782): polkit-gnome-1-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
** Message: applet now removed from the notification area

(xfce4-settings-helper:2799): xfce4-settings-helper-WARNING **: Failed to get the _NET_NUMBER_OF_DESKTOPS property.
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-ZrNusf/pkcs11: No such file or directory

(xfce4-indicator-plugin:2827): libindicator-WARNING **: IndicatorObject class does not have an accessible description.

(xfce4-indicator-plugin:2827): libindicator-WARNING **: IndicatorObject class does not have an accessible description.
** Message: using fallback from indicator to GtkStatusIcon
** Message: moving back from GtkStatusIcon to indicator

(xfce4-indicator-plugin:2827): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(xfce4-terminal:2996): Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed

(xfce4-terminal:3651): Gdk-CRITICAL **: IA__gdk_window_get_window_type: assertion `GDK_IS_WINDOW (window)' failed
thunar-volman: Unsupported USB device type.
thunar-volman: Unsupported USB device type.
thunar-volman: Unsupported USB device type.
thunar-volman: Unsupported input device type.
thunar-volman: Unsupported USB device type.
thunar-volman: Unsupported USB device type.
thunar-volman: Unsupported USB device type.

---

### Post by Toz on 2012-11-13
Make sure that you run:
```
pastebinit ~/.xsession-errors
```
...when you are logged into your GUI session.

There is nothing drastically wrong with that log file (aside from the warning messages). It would be interesting to see this log when the system is mis-behaving as initially posted.

---

### Post by Jacob72 on 2012-11-14
Really sorry, I was adding an 's' to '.xsession'.

Here is the pastebin:

[http://paste.ubuntu.com/1357885/](http://paste.ubuntu.com/1357885/)

---

### Post by Jacob72 on 2012-11-14
> It would be interesting to see this log when the system is mis-behaving as initially posted. 	

It happened again:

[http://paste.ubuntu.com/1358938/](http://paste.ubuntu.com/1358938/)

Also something else happened that is worrying, my mysql password no longer worked, all my local sites had the data base error message, I reset the password via terminal, though when I rebooted it did not work again??

Thanks

---

### Post by Toz on 2012-11-14
> xfce4-panel: No window manager registered on screen 0. To start the panel without this check, run with --disable-wm-check.


Looks like the window manager isn't starting, unfortunately there is nothing in the log file to indicate why.

I can't imagine how this could directly affect mysql.

---

### Post by Jacob72 on 2012-11-15
I think I may try a fresh install of Xubuntu 12.04

---

