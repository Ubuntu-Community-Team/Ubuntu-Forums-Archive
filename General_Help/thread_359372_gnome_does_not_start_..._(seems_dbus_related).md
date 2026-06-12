---
title: "gnome does not start ... (seems dbus related?)"
date: 2007-02-11
forum: General Help
---

### Post by miko3k on 2007-02-11
i had a strange kind of ubuntu mix (half dapper, half edgy mixed up with unofficial beryl stuff, kind of not working) and today i decided to fix it. I removed all unofficial packages, run distribution upgrade and after bunch of problems managed to start gdm.

Only thing working is an xterm session. Both gnome and failsafe gnome does not work. Failsafe is so kind it pops up window saying: Failed to open connection to session message bus: Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)

Here's my .xession_errors (added some tranlations - italic in squre brackets). I personally dislike lines saying something about returning -1 but I have no idea what they mean or how to fix it.
```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "miko"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/miko:/tmp/.ICE-unix/5840
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
evolution-alarm-notify-Message: Setting timeout for 73305 1171324800 1171251495
evolution-alarm-notify-Message:  Tue Feb 13 01:00:00 2007

evolution-alarm-notify-Message:  Mon Feb 12 04:38:15 2007

Varovanie správcu okien: Stratené spojenie s obrazovkou ':0.0'.
X server bol pravdepodobne vypnutý alebo ste zabili
správcu okien.
[[I]Window manager warning: Connection to screen ':0.0' lost.
X server was probably turned off or you killed window manager[/I]]
The application 'evolution-alarm-notify' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'gnome-cups-icon' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
alarm-notify.c:366 (alarm_notify_new) - Alarm Notify New 
 alarm-notify.c:302 (alarm_channel_setup) - Channel Setup
 alarm-notify.c:241 (alarm_notify_init) - Initing Alarm Notify
alarm-queue.c:1871 (alarm_queue_init)
alarm-queue.c:218 (queue_midnight_refresh) - Refresh at Tue Feb 13 01:00:00 2007
 
alarm-notify.c:218 (load_calendars) - Loading Calendar file:///home/miko/.evolution/calendar/local/system 
alarm-notify.c:454 (alarm_notify_add_calendar) - Calendar Open Async... 0x80a6710
alarm-notify.c:218 (load_calendars) - Loading Calendar contacts:/// 
alarm-notify.c:454 (alarm_notify_add_calendar) - Calendar Open Async... 0x80bb050
alarm-notify.c:218 (load_calendars) - Loading Calendar file:///home/miko/.evolution/tasks/local/system 
alarm-notify.c:454 (alarm_notify_add_calendar) - Calendar Open Async... 0x80bb0a0
alarm-notify.c:218 (load_calendars) - Loading Calendar file:///home/miko/.evolution/memos/local/system 
alarm-notify.c:454 (alarm_notify_add_calendar) - Calendar Open Async... 0x80bd2d0
alarm-notify.c:391 (cal_opened_cb) - Calendar Status 1B
alarm-queue.c:2053 (alarm_queue_add_client) - Posting a task
alarm-notify.c:391 (cal_opened_cb) - Calendar Status 1
alarm-queue.c:2053 (alarm_queue_add_client) - Posting a task
alarm-notify.c:347 (alarm_msg_received) - 0x80d9fc8: Received at thread b4de8ba0
alarm-queue.c:2004 (alarm_queue_add_async) - 0x80a6710
alarm-queue.c:560 (load_alarms_for_today) - From Mon Feb 12 04:38:17 2007
 to Mon Feb 12 04:38:17 2007
[* ... Stuff goes on .... not really interesting ... (i can't copy and paste more since xterm does not scroll widnow as i select text and i have no idea how executable for lovely gnome terminal is called:)) *]

```

'dbus-monitor' fails, 'dbus-monitor --system' gives usual result (probably not interesting)
```

signal sender=org.freedesktop.DBus -> dest=:1.13 path=/org/freedesktop/DBus; interface=org.freedesktop.DBus; member=NameAcquired
   string ":1.13"

```

As usual all lame reinstall-everyting tricks failed :)
Any suggestions ?

---

