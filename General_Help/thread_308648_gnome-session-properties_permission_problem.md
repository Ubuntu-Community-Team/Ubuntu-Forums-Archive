---
title: "gnome-session-properties permission problem"
date: 2006-11-28
forum: General Help
---

### Post by webellusion on 2006-11-28
Hi,

I have a simple problem.

I have installed gnome-compiz and gdesklets and wanted to add those to the startup.

I went to System > Preferences > Sessions > Add Program and added both of them (gdesklets and compiz-tray-icon).

When I exit the gnome-session-properties and return to it, they are not there . Running the same thing from terminal gives the following errors:

```
user@fjs:~$ gnome-session-properties

** (gnome-session-properties:8757): WARNING **: Could not save /home/user/.config/autostart/gdesklets.desktop file


** (gnome-session-properties:8757): WARNING **: Could not save /etc/xdg/autostart/update-notifier.desktop file


** (gnome-session-properties:8757): WARNING **: Could not save /etc/xdg/autostart/evolution-alarm-notify.desktop file


** (gnome-session-properties:8757): WARNING **: Could not save /usr/share/gnome/autostart/gnome-power-manager.desktop file


** (gnome-session-properties:8757): WARNING **: Could not save /etc/xdg/autostart/gnome-volume-manager.desktop file


** (gnome-session-properties:8757): WARNING **: Could not save /home/user/.config/autostart/beagled.desktop file


** (gnome-session-properties:8757): WARNING **: Could not save /usr/share/gnome/autostart/nm-applet.desktop file


```

I can see this as a permission problem but being new to Linux, I haven't got a clue on different type of permissions.

Further information is that startup could be added before installing programs through Automatix which messed things up.

Any commands that might solve this problem?

Thanks

---

### Post by dkeats on 2006-11-29
Did you perhaps have reinstalled, but keep your existing /homes?

I had the same problems and I did

$ chown dkeats /home/dkeats -R 

and this solved the problem for me. Your post here gave me the clue, so I am just reporting back what worked in my case.

regards
derek

---

### Post by dkeats on 2006-11-29
Sorry, that should be 

$ sudo chown YOURUSERNAME /homes/YOURUSERNAME

note you need to be root.
regards
derek

---

### Post by webellusion on 2006-11-29
> **dkeats said:**
> Sorry, that should be 

$ sudo chown YOURUSERNAME /homes/YOURUSERNAME

note you need to be root.
regards
derek


It didn't work. Seems like a bug in Edgy (or Automatix), unsure.

---

### Post by webellusion on 2006-11-29
> **webellusion said:**
> It didn't work. Seems like a bug in Edgy (or Automatix), unsure.

You are the man!

you led me to the path....


I tried "sudo chown -R user /home/user" and it worked like a charm.

I picked up the -R from "man chown" and its for 

```
-R, --recursive
              operate on files and directories recursively
```

Many Thanks.

---

### Post by strabes on 2006-11-29
that -R is always a useful feature especially when chmodding dirs

---

