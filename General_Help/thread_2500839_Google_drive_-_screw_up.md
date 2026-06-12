---
title: "Google drive - screw up"
date: 2024-09-13
forum: General Help
---

### Post by wilsojeffrey on 2024-09-13
So I followed some instructions to connect to google drive (latest LTS).

First was this command (I don’t even know how to get that command box in this forum).

sudo apt install gnome-online-accounts to receive the message that the latest version was already installed.

Next was

gnome-control-center online accounts 

I tried to follow the steps, it just kind of finished without any kind of message that it actually did finish, did not “connect” to google drive, and to top it all off, i’ve got an annoying icon appearing like an external drive, which shows my email address when I hover over it, that has a “mount” option which returns a message that it doesn’t have permission. I would like to either finish it correctly, or somehow undo what I did.

---

### Post by QIII on 2024-09-13
Would you be willing to share with us what "some instructions" you followed so we know what you did?

---

### Post by wilsojeffrey on 2024-09-13
[COLOR=#000000]sudo apt install gnome-online-accounts


followed by


[/COLOR][COLOR=#000000]gnome-control-center online-accounts[/COLOR][COLOR=#000000]


[/COLOR]

---

### Post by dragonfly41 on 2024-09-13
Well I went into Synaptic .. sudo synaptic .. and I see that at some point in my history of experiments I installed gnome-online-accounts (long forgotten, nestling there).

I ran the command
[COLOR=#000000][COLOR=#000000]
[/COLOR][/COLOR][COLOR=#000000][COLOR=#000000]gnome-control-center online-accounts

[/COLOR][/COLOR]and up pops a GUI with a list of accounts.


**P.S**. However .. I see in terminal these notes

(gnome-control-center:33501): ubuntu-cc-panel-WARNING **: 11:47:14.087: No yaru theme selected!


(gnome-control-center:33501): GLib-GObject-CRITICAL **: 11:47:14.264: g_signal_connect_object: assertion 'G_IS_OBJECT (gobject)' failed

[B]
P.P.S. [/B] Trying to open some accounts I hit further error messages relating to webkit .. and the desktop froze requiring reboot.

So enough of that for a game of soldiers. Experiment ends.

---

### Post by wilsojeffrey on 2024-09-13
Tried running it again and the errors are growing.

I can see a re-install in my future

---

