---
title: "g_dbus_proxy_new: assertion 'G_IS_DBUS_CONNECTION (connection)' failed"
date: 2018-10-07
forum: General Help
---

### Post by 3togo on 2018-10-07
Of no doubts, it is a very old question but pretty annoying. This has cursed me for years. It did not happen on every machine but once happened, you simply can't get rid of it except by clean installation. To me, this is definitely an overkill. 

I always wonder how to fix this.

Any pointers?

dbus-x11 has already been installed.

Case I:
gedit 
```
(gedit:19059): GLib-GIO-CRITICAL **: 18:25:47.959: g_dbus_proxy_new: assertion 'G_IS_DBUS_CONNECTION (connection)' failed

(gedit:19059): GLib-GIO-CRITICAL **: 18:25:47.959: g_dbus_proxy_new: assertion 'G_IS_DBUS_CONNECTION (connection)' failed

```

Case II:
NO_AT_BRIDGE=1 gedit
```
(gedit:19059): GLib-GIO-CRITICAL **: 18:25:47.959: g_dbus_proxy_new: assertion 'G_IS_DBUS_CONNECTION (connection)' failed

(gedit:19059): GLib-GIO-CRITICAL **: 18:25:47.959: g_dbus_proxy_new: assertion 'G_IS_DBUS_CONNECTION (connection)' failed

```

Case III:
dbus-launch --autolaunch=`cat /var/lib/dbus/machine-id` gedit
```
(gedit:19059): GLib-GIO-CRITICAL **: 18:25:47.959: g_dbus_proxy_new: assertion 'G_IS_DBUS_CONNECTION (connection)' failed

(gedit:19059): GLib-GIO-CRITICAL **: 18:25:47.959: g_dbus_proxy_new: assertion 'G_IS_DBUS_CONNECTION (connection)' failed

```

Case IV:
sudo -H gedit
```

NO ERROR

```

---

### Post by John Little on 2018-10-10
> **3togo said:**
> gedit 
```
(gedit:19059): GLib-GIO-CRITICAL **: 18:25:47.959: g_dbus_proxy_new: assertion 'G_IS_DBUS_CONNECTION (connection)' failed

(gedit:19059): GLib-GIO-CRITICAL **: 18:25:47.959: g_dbus_proxy_new: assertion 'G_IS_DBUS_CONNECTION (connection)' failed

```

I found this thread, annoyed that I was getting this with gvim.  With gedit I get it seven times, and with geany 40!  Every GTK app I've tried gives it at least once.

Looking at my install log, I saw I'd installed fcitx (to try and get an emoji picker).  I've purged that, and the G_IS_DBUS_CONNECTION errors have gone.

---

### Post by timomak on 2019-09-14
John, do you mean  that the problem was fctix ?
I have the same issue with leafpad when trying to edit double click and other preferences with sysctl file, in lubuntu 18.04.3 (just a week instalation).
I admit that in many cases there is a gap in support on issues that are difficult to solve.

---

### Post by John Little on 2019-09-14
> **timomak said:**
> John, do you mean  that the problem was fctix ?
Yes, indeed.

---

### Post by timomak on 2019-10-14
Sorry being late to reply.
There is this bug too, [Bug #1770129 &#8220;G_IS_DBUS_CONNECTION (connection)' failed&#8221; : Bugs : leafpad package : Ubuntu]("https://bugs.launchpad.net/ubuntu/+source/leafpad/+bug/1770129") 
Do you know if this issue is fixed?

---

