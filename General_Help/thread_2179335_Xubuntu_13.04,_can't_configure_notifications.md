---
title: "Xubuntu 13.04, can't configure notifications"
date: 2013-10-07
forum: General Help
---

### Post by han2 on 2013-10-07
Hello,

For some reason my notification settings are being ignored. No matter what I change (theme, default position, time or opacity), notifications keep appearing and acting the same way.

Any idea about how could I solve this?

Regards.

---

### Post by Toz on 2013-10-07
Where are you trying to change the notification settings? From the Xfce Settings Manager? Perhaps you've got another notification daemon installed and running? Open a terminal window, type in the following commands and post back the results:
```
ps -ef | grep -i notif
```
```
ps -ef | grep -i dunst
```
...and
```
dpkg -l | grep -i notif
```
```
dpkg -l | grep -i dunst
```
Lets see whats running and installed.

---

### Post by han2 on 2013-10-08
Yes, I'm trying to change it in Xfce Settings Manager. 

Here's what I got:

```
~$ ps -ef | grep -i notif

root        44     2  0 10:24 ?        00:00:00 [fsnotify_mark]
han       9100     1  0 10:52 ?        00:00:01 /usr/lib/x86_64-linux-gnu/notify-osd
han       9134     1  0 10:52 ?        00:00:00 update-notifier
han       9160  9095  0 10:52 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper /usr/lib/x86_64-linux-gnu/xfce4/panel/plugins/libsystray.so 6 23068703 systray Notification Area Area where notification icons appear 
han      32257 32207  0 11:21 pts/0    00:00:00 grep --color=auto -i notif

~$ ps -ef | grep -i dunst


han       5660 32207  0 11:25 pts/0    00:00:00 grep --color=auto -i dunst

~$ dpkg -l | grep -i notif


ii  gir1.2-notify-0.7                             0.7.5-2                                amd64        sends desktop notifications to a notification daemon (Introspection files)
ii  libevent-2.0-5:amd64                          2.0.19-stable-3                        amd64        Asynchronous event notification library
ii  libgtk2-notify-perl                           0.05-3build1                           amd64        Perl interface to libnotify
ii  libnotify-bin                                 0.7.5-2                                amd64        sends desktop notifications to a notification daemon (Utilities)
ii  libnotify0.4-cil                              0.4.0~r3032-6                          all          CLI library for desktop notifications
ii  libnotify4:amd64                              0.7.5-2                                amd64        sends desktop notifications to a notification daemon
ii  libstartup-notification0:amd64                0.12-2                                 amd64        library for program launch feedback (shared library)
ii  libzephyr4                                    3.0.2-2                                amd64        Project Athena's notification service - non-Kerberos libraries
ii  notify-osd                                    0.9.35daily12.11.28-0ubuntu1           amd64        daemon that displays passive pop-up notifications
ii  notify-osd-icons                              0.7                                    all          Notify-OSD icons
ii  pidgin-libnotify                              0.14-9ubuntu1                          amd64        display notification bubbles in pidgin
ii  python-notify                                 0.1.1-3ubuntu1                         amd64        Python bindings for libnotify
ii  python-pyinotify                              0.9.3-1.1ubuntu1                       all          simple Linux inotify Python bindings
ii  update-notifier                               0.134                                  amd64        Daemon which notifies about package updates
ii  update-notifier-common                        0.134                                  all          Files shared between update-notifier and other packages
ii  vlc-plugin-notify                             2.0.8-0ubuntu0.13.04.1                 amd64        LibNotify plugin for VLC
ii  xfce4-notifyd                                 0.2.2-3                                amd64        simple, visually-appealing notification daemon for Xfce
```

With "dpkg -l | grep -i dunst" I got nothing.

---

### Post by Toz on 2013-10-08
You have notify-osd installed and running and its taking over precedence from xfce4-notifyd (the Xfce notification deamon), therefore changing the settings in the Xfce settings manager won't work. 

There may be another settings app for notify-osd somewhere (not sure exactly where) that you could use to configure the notifications, or you can remove it (be careful of the dependencies that may be removed as well), or you can [disable notify-osd]("http://ubuntuforums.org/showthread.php?t=1894914&p=11535440&viewfull=1#post11535440") and let the Xfce notification daemon take over.

---

### Post by han2 on 2013-10-08
Thankz, Toz.
 
I used the command "[COLOR=#000000][FONT=Ubuntu Mono]sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled[/FONT][/COLOR]" from the thread you linked, and now is working well.

Regards.

---

