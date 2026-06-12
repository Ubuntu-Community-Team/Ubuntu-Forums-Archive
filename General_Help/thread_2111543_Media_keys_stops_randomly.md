---
title: "Media keys stops randomly"
date: 2013-02-02
forum: General Help
---

### Post by quirino77 on 2013-02-02
I'm using Ubuntu 12.04.
After sometime powered on (minutes, hours, days...) the media keys stop working untill i reboot. All the others works fine. I have this keys on the keyboard and on a remote. Both do not work.

How can i diagnose what goes wrong that the keys stops so i could try to fix?

org.gnome.settings-daemon.plugins.media-keys is on.

Thank's.

---

### Post by tgalati4 on 2013-02-02
Try logging out then logging back in and see if the keys work.  If so, then there is a bug in the Xorg keymapping system.  If only a cold reboot will bring the keys back, then it could be a BIOS or hardware problem.  I presume these are the special media keys apart from the regular keyboard?

Is this a laptop or desktop machine?

---

### Post by quirino77 on 2013-02-02
Thanks.
A logout has worked. I even forgot to try since i use autologon and no one  more use my pc. What should i do now?

These are the play, next, previous, vol+, vol-, etc. I have then on the keyboard and on a remote control (my pc also a xbmc, thats why this bothers me).

---

### Post by Bashing-om on 2013-02-02
quirino77; Hi !

Have you looked in the logs for an indication of what Xorg/Xserver is not seeing ?
In particular the log file /var/log/Xorg.0.log .

[INDENT][INDENT][INDENT]hth

[/INDENT][/INDENT][/INDENT]

---

### Post by tgalati4 on 2013-02-02
Also check:

```
cat ~/.xsession-errors
```

So you know that restarting xorg (by logging out and logging in) will reset the keymap.  Pay attention to which applications that you load.  Some multimedia applications redefine the special media keys and take them over.  This breaks the mapping for xorg so the keys don't work in other applications.

```
man xmodmap
```

Once you have identified the bad actor, you can look for work arounds.  One work around would be to use xmodmap to reinitialize the keymappings after running the bad actor.

Because keymaps get defined in several places in linux, it may take a while to figure out what is broken and how to fix it.

---

### Post by quirino77 on 2013-02-12
Strange. It is not happening anymore. Good, but i'm curious about it. The only thing i can imagine is the XBMC itself. I updated it to the new version. But many times i used (the old) XBMC with no problem.

Thank's for helping me. I really appreciate it. If the problem returns, i will check what you have suggested and let you know.

---

### Post by tgalati4 on 2013-02-12
If it happens again, immediately check dmesg:

Open a terminal:

```
dmesg | more
```

Spacebar to page forward, "q" to quit.  Look for any weird behavior and what is happening on the last page:

```
dmesg | tail -50
```

Also run xev and press the multimedia keys and take note of the keycodes:

```
xev
```

If the keycodes don't show up, then it could be a BIOS or hardware problem.  In that case, look into flashing new BIOS onto your machine.

---

