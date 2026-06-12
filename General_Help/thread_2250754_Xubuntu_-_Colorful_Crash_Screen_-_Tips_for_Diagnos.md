---
title: "Xubuntu - Colorful Crash Screen - Tips for Diagnosis?"
date: 2014-10-30
forum: General Help
---

### Post by eth02 on 2014-10-30
I installed Xubuntu 14.04 on this desktop at work. It routinely crashes, and when it does it locks up and the screen gets real colorful. (I've attached a couple of examples.)

I've poked around in /var/log a little bit, but I'm not really sure what I'm looking for. A little help in narrowing down which logs to look in first, and what I might want to look for, would be really helpful.

Thanks!

[ATTACH=CONFIG]257619[/ATTACH]


--------------------

Xubuntu 14.04
Kernel 3.13.0-39-generic
eMachines AMD Athlon 2850e Desktop

---

### Post by Habitual on 2014-10-30
look in/at ~/.xsession-errors
There may be a clue there.

---

### Post by Bucky Ball on 2014-10-30
Welcome. Routinely crashes? What's the routine? Please give more information about when it crashes and what you're doing at the time (in other words can you replicate the crash). When it crashes, can you hit ctl+alt+F1 and log in at a CLI? If so, login and post the result of this command:

dmesg

---

### Post by eth02 on 2014-11-03
I will look through ~/.xsession-errors and see if anything sticks out.

---

### Post by eth02 on 2014-11-03
Routinely as in it crashes at least once a workday, sometimes  (like today) it crashes six or seven times. It's a low-spec machine, so I  tend to use one application at a time. It tends to crash when I am  starting the browser (Firefox), but also happens when Chrome or Midori  are running, or no browser at all. It exhibits the same behavior under  Xfce, Lxqt, and Mate. It's difficult to predict when it's going to  happen. Once it happens you can't get into another terminal session, or  do anything at all, except power the machine off with the power button.

Thanks to you both for your help!

---

### Post by eth02 on 2014-11-03
Here's the contents of .xsession-errors. Nothing too notable?

```

openConnection: connect: No such file or directory
cannot connect to brltty at :0
Script for none started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
Script for none started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
mate-session[1586]: WARNING: Could not parse desktop file /home/room3/.config/autostart/screensaver-settings.desktop: Key file does not have key 'Type'
mate-session[1586]: GLib-GObject-CRITICAL: object GsmAutostartApp 0x2587c10 finalized while still in-construction
mate-session[1586]: GLib-GObject-CRITICAL: Custom constructor for class GsmAutostartApp returned NULL (which is invalid). Please use GInitable instead.
mate-session[1586]: WARNING: could not read /home/room3/.config/autostart/screensaver-settings.desktop

** (update-notifier:1821): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-jiqRNPGHCw: Connection refused
mate-session[1586]: WARNING: Could not launch application 'light-locker.desktop': Unable to start application: Text was empty (or contained only whitespace)

(process:1867): Indicator-Power-WARNING **: Fail to query backlight devices.

** (mate-power-manager:1834): WARNING **: levels is 0!
** Message: Initializing gksu extension...
The setuid sandbox is not running as root. Common causes:
  * An unprivileged process using ptrace on it, like a debugger.
  * A parent process set prctl(PR_SET_NO_NEW_PRIVS, ...)
Failed to move to new namespace: PID namespaces supported, Network namespace supported, but failed: errno = Operation not permitted
[1840:2220:1103/142007:ERROR:print_backend_cups.cc(168)] CUPS: Failed to get PPD, printer name: HP-Officejet-6200-series

(process:2245): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
[1840:2220:1103/142010:ERROR:print_backend_cups.cc(168)] CUPS: Failed to get PPD, printer name: HP-Officejet-6200-series
[1840:2220:1103/142010:ERROR:printer_job_handler.cc(710)] Failed to get printer caps and defaults, printer name: \\\HP-Officejet-6200-series

** (update-notifier:1821): WARNING **: log file empty (logrotate?) /var/log/dpkg.log

** (update-notifier:1821): WARNING **: log file empty (logrotate?) /var/log/apt/term.log
[1840:2220:1103/142510:ERROR:print_backend_cups.cc(168)] CUPS: Failed to get PPD, printer name: HP-Officejet-6200-series
Window manager warning: Log level 8: Source ID 126 was not found when attempting to remove it

```

---

