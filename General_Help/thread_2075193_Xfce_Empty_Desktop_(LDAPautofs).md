---
title: "Xfce Empty Desktop (LDAP/autofs)"
date: 2012-10-23
forum: General Help
---

### Post by Alboroto on 2012-10-23
Hi! I have something similar:
```
openConnection: connect: No such file or directory
cannot connect to brltty at :0

(polkit-gnome-authentication-agent-1:1567): GLib-CRITICAL **: g_variant_new_string: assertion `string != NULL' failed

(polkit-gnome-authentication-agent-1:1567): polkit-gnome-1-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-rVrgat/pkcs11: &#1053;&#1077;&#1090; &#1090;&#1072;&#1082;&#1086;&#1075;&#1086; &#1092;&#1072;&#1081;&#1083;&#1072; &#1080;&#1083;&#1080; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072;
** Message: applet now removed from the notification area
** Message: using fallback from indicator to GtkStatusIcon
** Message: applet now embedded in the notification area

(xfce4-indicator-plugin:1629): libindicator-WARNING **: IndicatorObject class does not have an accessible description.

(xfce4-indicator-plugin:1629): libindicator-WARNING **: IndicatorObject class does not have an accessible description.

(xfce4-indicator-plugin:1629): Gtk-CRITICAL **: IA__gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed
** Message: moving back from GtkStatusIcon to indicator
** Message: applet now removed from the notification area

(xfce4-indicator-plugin:1629): Indicator-Application-WARNING **: Unable to get application list
```

I can see only mouse and clear desktop after login screen. I've tried to find what is wrong(ctrl+alt+F1) and I found(sudo lsof /home/$user) gsettings process, that was working with .xsession-errors. I've killed it and get back to tty7. Everithing looks fine, but I need to do it every time I want to login=(

---

### Post by Toz on 2012-10-23
Moderator Note: Since this issue is slightly different from the thread you posted in, I have moved it to it's own thread.

Hello and welcome to the forums.

There doesn't appear to be anything wrong in your log file.
[LIST=1]
[*]Is this a Xubuntu or an Xfce on Ubuntu install? 
[*]What version?
[*]Has the desktop ever showed up?
[*]How long do you wait for the desktop to show up? Perhaps there is a delay.
[/LIST]

---

### Post by Alboroto on 2012-10-23
This is xubuntu 12.04.
I'm trying to mount /home directory with autofs and ldap authorization. Everything is ok except gui. Desktop showed up when I've been using local /home, also  it works good at first start after shutdown.
 I wait about few minutes, nothing changes:( kill-9 gsettings helps only:(

---

### Post by Toz on 2012-10-23
It looks like this is a known bug. See: [https://bugs.launchpad.net/ubuntu/+source/at-spi2-core/+bug/870874]("https://bugs.launchpad.net/ubuntu/+source/at-spi2-core/+bug/870874"). There are a couple of potential solutions noted there.

EDIT: Also updated title of this thread to more accurately reflect the issue.

---

### Post by Alboroto on 2012-10-24
> **Toz said:**
> It looks like this is a known bug. See: [https://bugs.launchpad.net/ubuntu/+source/at-spi2-core/+bug/870874]("https://bugs.launchpad.net/ubuntu/+source/at-spi2-core/+bug/870874"). There are a couple of potential solutions noted there.

EDIT: Also updated title of this thread to more accurately reflect the issue.
Thank you very much for help!=)
I've installed nscd and this solved the bug!

---

