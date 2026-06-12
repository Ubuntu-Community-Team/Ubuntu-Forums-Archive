---
title: "[SOLVED] Desktop goes black after login"
date: 2008-07-06
forum: General Help
---

### Post by TonyGould on 2008-07-06
On hardy I have this *intermittent* problem on my laptop. It seems to happen anywhere between 1/3 and 2/3 of the logins, but is getting more frequent if anything. The desktop is black, and I've lost all my shortcuts.

The login screen itself is fine. Everything else is fine, including the panels above & below the desktop. Starting up windows is fine. Compiz effects work well too.

Any ideas?

Tony.

---

### Post by Tomatz on 2008-07-06
> **TonyGould said:**
> On hardy I have this *intermittent* problem on my laptop. It seems to happen anywhere between 1/3 and 2/3 of the logins, but is getting more frequent if anything. The desktop is black, and I've lost all my shortcuts.

The login screen itself is fine. Everything else is fine, including the panels above & below the desktop. Starting up windows is fine. Compiz effects work well too.

Any ideas?

Tony.

Something is making nautilus hang. When it happens try:
```

killall nautilus
```

---

### Post by TonyGould on 2008-07-06
> **Tomatz said:**
> Something is making nautilus hang. When it happens try:
```

killall nautilus
```

As luck would have it, took 6 reboots to get the problem happening again, grrr.

Anyway, good call. The desktop comes back immediately, the mouse hangs and windows go grey for a few seconds, then my mouse comes back, and a File Browser window pops up in my home folder.

(this probably explains why logging out and in also fixes the problem).

---

### Post by forger on 2008-07-06
yeah, the default file browser in gnome is called nautilus :)
What happens if you create another user and login to that one? try create a new test user and use that for some days, see if the problem re-appears.

If it doesn't, then something in your sessions or gnome config is definitely giving you some hard time. You could try clearing out ~/.config/ but this means that **[COLOR="Red"]you lose most of your settings[/COLOR]** with applications that have to do with gnome (totem, deluge, sound juicer, screenlets, endless list...)

---

### Post by TonyGould on 2008-07-06
> **forger said:**
> What happens if you create another user and login to that one? try create a new test user and use that for some days, see if the problem re-appears.

If it doesn't, then something in your sessions or gnome config is definitely giving you some hard time. You could try clearing out ~/.config/ but this means that **[COLOR="Red"]you lose most of your settings[/COLOR]** with applications that have to do with gnome (totem, deluge, sound juicer, screenlets, endless list...)

thanks. Your hypothesis is that something is rotten in .config? So rather than logging in as another user (which would mean I'd lose access to Thunderbird profiles etc when I was logged in as the other user), I'm assuming it would be just as easy to manually turn things off like compiz, or take a copy of .config and then hack around with it or just delete it altogether. There's very little in there that I care about to be honest (see below). For example, I've turned off all the autostart apps already.

Also, it seems like there's some sort of a race condition going on here: depending on exactly which processes run fastest on the initial login, then Nautilus hangs and needs to be killed off. Would configuration files explain a race condition? Or should I be looking at logs or maybe which processes are running to see if something is blocking Nautilus, e.g. what can I kill that would allow Nautilus to start running again? Or am I going completely up the wrong tree?

Tony

```

tony@rizeon:~$ find .config
.config
.config/user-dirs.dirs
.config/menus
.config/menus/applications.menu.undo-15
.config/menus/applications.menu.undo-14
.config/menus/applications.menu
.config/menus/applications.menu.undo-11
.config/menus/settings.menu
.config/menus/applications.menu.undo-16
.config/menus/applications.menu.undo-13
.config/menus/applications.menu.undo-12
.config/menus/applications.menu.undo-10
.config/user-dirs.locale
.config/compiz
.config/compiz/compizconfig
.config/compiz/compizconfig/config
.config/Trolltech.conf
.config/gtk-2.0
.config/gtk-2.0/gtkfilechooser.ini
.config/tracker
.config/tracker/tracker-applet.cfg
.config/tracker/tracker.cfg
.config/totem
.config/totem/state.ini
.config/autostart
.config/autostart/evolution-alarm-notify.desktop
.config/autostart/bluetooth-applet.desktop
.config/autostart/user-dirs-update-gtk.desktop
.config/autostart/gnome-at-session.desktop

```

---

### Post by Tomatz on 2008-07-06
Try this (one at a time consecutively):

```
mkdir OLD_CONFIGS

mv .gnome* OLD_CONFIGS # GnomeSettings

mv .gconf* OLD_CONFIGS # GnomeGconfdSettings

mv .nautilus OLD_CONFIGS # NautilusSettings

mv .metacity OLD_CONFIGS # Metacity

```

**Ctrl Alt Bkspace** ;)

---

### Post by forger on 2008-07-06
Tomatz's way should do it :)

---

### Post by TonyGould on 2008-07-07
Thanks guys. I'm pretty sure that it's something under .nautilus. Unfortunately Nautilus writes its settings at logout and the only way I could find to get rid was to put rm code into rc.local. Anyway since starting out with brute force removing the whole directory, and more recently by removing everything apart from the file containing my desktop shortcuts, I haven't had the problem. The code I have now in rc.local is
```

find ~tony/.nautilus -type f ! -name 'file:%2F%2F%2Fhome%2Ftony%2FDesktop.xml' | xargs rm

```

I *suspect* the file that's causing it is called .nautilus/metafiles/x-nautilus-desktop. This lists all the desktop shortcuts that Nautilus automatically mounts, like the Windows drives, USB drives, etc. It's possible that it's not getting access to the USB drives: support for these can be a bit flakey. I might try refining what I delete to target that one (it's completely autogenerated anyway). If that proves it, should I report this as a bug?

Tony.

---

