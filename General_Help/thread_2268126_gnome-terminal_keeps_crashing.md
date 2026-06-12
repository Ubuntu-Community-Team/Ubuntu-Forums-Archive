---
title: "gnome-terminal keeps crashing"
date: 2015-03-06
forum: General Help
---

### Post by Sam_Nazarko on 2015-03-06
Hi

I am running Ubuntu with a Gnome Desktop and my Terminal keeps closing. There are a couple of things I can do to always cause a crash:

[LIST]
[*]run 'dmesg'
[*]Resize the terminal window
[/LIST]

Nothing is showing in /var/log/syslog related to a crash

I tried to gdb --attach=$(pidof gnome-terminal) but this freezes gnome-terminal so I can't crash it anymore and see what may be happening

CTRL ALT f2 and running the same dmesg is fine. I can also crash the Terminal with /bin/bash -c dmesg. Note that crashes are not limited to running dmesg, this is just a guaranteed crash. I can open nano and then use it for a couple of seconds and it will crash too

I don't know how to diagnose this, so all help appreciated

Sam

---

### Post by Sam_Nazarko on 2015-03-06
I have noticed 'ls' too will cause Terminal to instantly close

---

### Post by Sam_Nazarko on 2015-03-06
Managed to attach gdb and realised /tmp had wrong owner

---

