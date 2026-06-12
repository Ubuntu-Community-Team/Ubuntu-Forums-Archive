---
title: "Gnome Shell filling syslog"
date: 2023-06-26
forum: General Help
---

### Post by prosmart on 2023-06-26
Greetings

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292418&stc=1[/IMG]

Have a very strange problem that appeared recently (at least I had not noticed it).

Started work this morning and had nothing but four black monitors and a mouse cursor.

When I eventually got in via a TTY prompt, I found that the syslog file was over 400GB and the system had died trying to protect it.

The first problem is this message repeated hundreds of times per minute:

```
Jun 26 07:38:17 nigel-xps gnome-shell[2512]: == Stack trace for context 0x562838948170 ==
Jun 26 07:38:17 nigel-xps gnome-shell[2512]: Attempting to run a JS callback during garbage collection. This is most likely caused by destroying a Clutter actor or GTK widget with ::destroy signal connected, or using the destroy(), dispose(), or remove() vfuncs. Because it would crash the application, it has been blocked.
Jun 26 07:38:17 nigel-xps gnome-shell[2512]: The offending callback was SourceFunc().
Jun 26 07:38:17 nigel-xps gnome-shell[2512]: Attempting to run a JS callback during garbage collection. This is most likely caused by destroying a Clutter actor or GTK widget with ::destroy signal connected, or using the destroy(), dispose(), or remove() vfuncs. Because it would crash the application, it has been blocked.
Jun 26 07:38:17 nigel-xps gnome-shell[2512]: == Stack trace for context 0x562838948170 ==
Jun 26 07:38:17 nigel-xps gnome-shell[2512]: == Stack trace for context 0x562838948170 ==
Jun 26 07:38:17 nigel-xps gnome-shell[2512]: The offending callback was SourceFunc().
Jun 26 07:38:17 nigel-xps gnome-shell[2512]: == Stack trace for context 0x562838948170 ==
Jun 26 07:38:17 nigel-xps gnome-shell[2512]: Attempting to run a JS callback during garbage collection. This is most likely caused by destroying a Clutter actor or GTK widget with ::destroy signal connected, or using the destroy(), dispose(), or remove() vfuncs. Because it would crash the application, it has been blocked.
Jun 26 07:38:17 nigel-xps gnome-shell[2512]: == Stack trace for context 0x562838948170 ==
Jun 26 07:38:17 nigel-xps gnome-shell[2512]: == Stack trace for context 0x562838948170 ==
Jun 26 07:38:17 nigel-xps gnome-shell[2512]: The offending callback was SourceFunc().
Jun 26 07:38:17 nigel-xps gnome-shell[2512]: Attempting to run a JS callback during garbage collection. This is most likely caused by destroying a Clutter actor or GTK widget with ::destroy signal connected, or using the destroy(), dispose(), or remove() vfuncs. Because it would crash the application, it has been blocked.
Jun 26 07:38:17 nigel-xps gnome-shell[2512]: == Stack trace for context 0x562838948170 ==
Jun 26 07:38:17 nigel-xps gnome-shell[2512]: == Stack trace for context 0x562838948170 ==
Jun 26 07:38:17 nigel-xps gnome-shell[2512]: The offending callback was SourceFunc().
Jun 26 07:38:17 nigel-xps gnome-shell[2512]: == Stack trace for context 0x562838948170 ==
Jun 26 07:38:17 nigel-xps gnome-shell[2512]: == Stack trace for context 0x562838948170 ==
Jun 26 07:38:17 nigel-xps gnome-shell[2512]: Attempting to run a JS callback during garbage collection. This is most likely caused by destroying a Clutter actor or GTK widget with ::destroy signal connected, or using the destroy(), dispose(), or remove() vfuncs. Because it would crash the application, it has been blocked.
Jun 26 07:38:17 nigel-xps gnome-shell[2512]: The offending callback was SourceFunc().
Jun 26 07:38:17 nigel-xps gnome-shell[2512]: == Stack trace for context 0x562838948170 ==
Jun 26 07:38:17 nigel-xps gnome-shell[2512]: == Stack trace for context 0x562838948170 ==
Jun 26 07:38:17 nigel-xps gnome-shell[2512]: Attempting to run a JS callback during garbage collection. This is most likely caused by destroying a Clutter actor or GTK widget with ::destroy signal connected, or using the destroy(), dispose(), or remove() vfuncs. Because it would crash the application, it has been blocked.
Jun 26 07:38:17 nigel-xps gnome-shell[2512]: == Stack trace for context 0x562838948170 ==
Jun 26 07:38:17 nigel-xps gnome-shell[2512]: == Stack trace for context 0x562838948170 ==
Jun 26 07:38:17 nigel-xps gnome-shell[2512]: The offending callback was SourceFunc().
Jun 26 07:38:17 nigel-xps gnome-shell[2512]: Attempting to run a JS callback during garbage collection. This is most likely caused by destroying a Clutter actor or GTK widget with ::destroy signal connected, or using the destroy(), dispose(), or remove() vfuncs. Because it would crash the application, it has been blocked.
Jun 26 07:38:17 nigel-xps gnome-shell[2512]: == Stack trace for context 0x562838948170 ==
Jun 26 07:38:17 nigel-xps gnome-shell[2512]: The offending callback was SourceFunc().
Jun 26 07:38:17 nigel-xps gnome-shell[2512]: == Stack trace for context 0x562838948170 ==
Jun 26 07:38:17 nigel-xps gnome-shell[2512]: == Stack trace for context 0x562838948170 ==
```

I'm guessing the gnome shell issues might be caused by on of the extensions I have installed:

```
apps-menu@gnome-shell-extensions.gcampax.github.com
arcmenu@arcmenu.com
burn-my-windows@schneegans.github.com
dash-to-dock-cosmic-@halfmexicanhalfamazing@gmail.com
dash-to-panel@jderose9.github.com
space-bar@luchrioh
Vitals@CoreCoding.com
```

Q1: Can anyone suggest how to identify the culprit?

Q2: Does anyone know how to reduce the amount of logging that Thunderbird is spewing into syslog?

With thanks

Nigel.

---

### Post by Rubi1200 on 2023-07-02
There is a launchpad bug report about this:
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1908429](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1908429)

I would start there to see if any solutions/workarounds are available.

Could be Intel graphics related or browser related.

Hope this helps.

---

