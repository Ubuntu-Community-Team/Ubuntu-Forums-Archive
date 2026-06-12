---
title: "Vino-server numpad won't work"
date: 2024-05-22
forum: General Help
---

### Post by yourname98 on 2024-05-22
I installed Ubuntu 22.04 and enabled remote desktop in VNC mode (vino-server). I connect from other machines (Ubuntu and Windows) and the numeric keypad does not work when NUMLOCK is activated (when it should type numbers).

When NUMLOCK is disabled on the observer station, the numeric keypad works, i.e. 4="left arrow", 3="page down", etc.

This problem is identical regardless of the VNC client I use (TigerVNC, Remmina, gvncviewer, UltraVNC for Windows) and the OS of the observer station (Ubuntu 18.04, 22.04, Windows 10).

Three diagnostic points.

- Point 1:
[LIST]
[*]On the observed station I run the “screenkey” command
[*]On the observer station I type "b"
[*]On the station observed I see "Num.Lock(off) b Num.Lock(on)" (it does it with each key pressed)
[/LIST]

- Point 2: the problem arises with the default window manager of Ubuntu and Xfce.

- Point 3: for comparison, on an Ubuntu 18.04 machine with remote desktop in VNC mode (vino-server), the numeric keypad works perfectly well.


So to summarize, I enabled remote desktop on my machines:
[LIST]
[*]2 Ubuntu 22.04 machines where the numpad does not work
[*]1 Ubuntu 18.04 machine where the numpad works fine. (Windows 10 machine is a VirtualBox VM on Ubuntu 22.04)
[/LIST]

Any idea ?

---

### Post by &amp;KyT$0P# on 2024-05-22
Do you specifically need to use vino-server?

I had keyboard issues like this with vino-server and ended up solving it by switching the server to TigerVNC (in my case [FONT=Courier New]X0tigervnc[/FONT], package [FONT=Courier New]tigervnc-scraping-server[/FONT]) and using its [[FONT=Courier New]RawKeyboard[/FONT] option]("https://manpages.ubuntu.com/manpages/jammy/en/man1/X0tigervnc.1.html").

---

### Post by yourname98 on 2024-05-23
I use the "remote desktop" feature shipped in Ubuntu. It happens to use "vino-server"...

---

