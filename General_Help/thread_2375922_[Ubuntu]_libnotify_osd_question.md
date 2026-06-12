---
title: "[Ubuntu] libnotify osd question"
date: 2017-10-28
forum: General Help
---

### Post by jtodd.fr on 2017-10-28
[SUP]When searching on the internet for volume indicator, I come across that Ubuntu uses libnotify osd for displaying information, including sound, and brightness. However checking with command 
```

dpkg -S notify | grep osd | grep -v svg

```
I can't find any script that is used to trigger volume or brightness information. Any places that I should check?  

Thanks[/SUP]
```
notify-osd: /usr/share/notify-osd/icons/hicolor
diversion by notify-osd from: /usr/share/dbus-1/services/org.freedesktop.Notifications.service
diversion by notify-osd to: /usr/share/dbus-1/services/org.freedesktop.Notifications.service.notify-osd
notify-osd: /usr/share/doc/notify-osd/changelog.Debian.gz
notify-osd: /usr/share/notify-osd/icons/hicolor/scalable/status/README
gnome-orca: /usr/lib/python3/dist-packages/orca/scripts/apps/notify-osd/__init__.py
notify-osd-icons: /usr/share/notify-osd/icons/Humanity/scalable/status
notify-osd: /usr/share/GConf/gsettings/notify-osd.convert
notify-osd, notify-osd-icons: /usr/share/notify-osd
notify-osd: /usr/share/apport/package-hooks/source_notify-osd.py
notify-osd-icons: /usr/share/doc/notify-osd-icons/copyright
notify-osd: /usr/share/doc/notify-osd
gnome-orca: /usr/lib/python3/dist-packages/orca/scripts/apps/notify-osd
gnome-orca: /usr/lib/python3/dist-packages/orca/scripts/apps/notify-osd/script.py
notify-osd-icons: /usr/share/notify-osd/icons/Humanity
notify-osd-icons: /usr/share/notify-osd/icons/Humanity/scalable
notify-osd: /usr/share/notify-osd/icons/hicolor/scalable/status
notify-osd: /usr/lib/x86_64-linux-gnu/notify-osd
notify-osd-icons: /usr/share/doc/notify-osd-icons/changelog.Debian.gz
notify-osd: /usr/share/doc/notify-osd/copyright
notify-osd-icons: /usr/share/doc/notify-osd-icons
notify-osd, notify-osd-icons: /usr/share/notify-osd/icons
notify-osd: /usr/share/notify-osd/icons/hicolor/scalable



```

---

### Post by ian-weisser on 2017-10-28
It's not a script.
Scripts are only one of many ways to do something.

In this case, libnotify listens on an internal inter-process communication echange called "dbus" for certain events, like new-mail, brightness-change, download-complete, etc.
Some applications boradcast on dbus, others listen.

---

### Post by jtodd.fr on 2017-10-28
Thanks for explanation. Which command, or binary is used to listen and trigger notifying sound/ brightness indicator for displaying status on the screen? 

Thank you again for your help.

---

### Post by ian-weisser on 2017-10-28
Seems like an [XY Problem]("https://meta.stackexchange.com/questions/66377/what-is-the-xy-problem"). What, exactly, are you trying to accomplish?

---

### Post by jtodd.fr on 2017-10-31
> **ian-weisser said:**
> Seems like an [XY Problem]("https://meta.stackexchange.com/questions/66377/what-is-the-xy-problem"). What, exactly, are you trying to accomplish?

I want to switch to i3 wm. But I miss the feature in Unity where pressing F1, F2, F3 or F12, F11 will display related status like sound and brightness. I searched a bit and noticed I can display message with icon by command like 

```

notify-send "WiFi connection lost" -i notification-network-wireless-disconnected
```

[https://wiki.ubuntu.com/NotificationDevelopmentGuidelines#Help.21_No_libnotify_bindings_for_language_X](https://wiki.ubuntu.com/NotificationDevelopmentGuidelines#Help.21_No_libnotify_bindings_for_language_X)

But I am still not sure how to display volume status (the scroll bar that represents whether the volume sound is loud or soft).

---

