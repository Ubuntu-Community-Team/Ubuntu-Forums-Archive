---
title: "tsclient freezes laptop?"
date: 2008-02-24
forum: General Help
---

### Post by lawr_rawr on 2008-02-24
I'm running Gutsy on a Dell XPS M1330, and using Cisco VPN client to connect to work. When I use the Terminal Services Client to connect to a Windows server, after a few seconds I get a crazy freeze -- the computer is completely non-responsive. I can't move the mouse or use the keyboard, and the Caps Lock and Num Lock lights blink in unision. I have to power down the laptop. 

Has anyone else seen this? It doesn't happen with GnomeRDP; just the default tsclient. I also don't remember this happening on my previous laptop, and can't find any other posts with similar issues.

---

### Post by dad311 on 2008-02-24
I dont have this exact problem, but may be related.  I access an XP Laptop using rdesktop & Feisty.  Sometimes while using  XP internet explorer, my Ubuntu CPU will hit 100% and I have to close the rdesktop program and restart it.

---

### Post by lawr_rawr on 2008-02-25
Hmm, don't think it's the exact same problem. When mine stops responding, nothing works on the laptop except for the power button. No keyboard or mouse, so I can't even shutdown the app normally.

---

### Post by mkalle on 2008-02-26
Hi

i have the same symtoms, but a HP/Compaq 6910p and i am using kubuntu hardy instead of gnome.
its driving me nuts!
it will just get me far enough to see my desktop on my windows client, and then everything stops.
i cant get into another shell with alt+f1 or ctrl+alt+f1 and alt+ctrl+backspace does nothing.
i am going to make bug on launchpad

---

### Post by mkalle on 2008-02-27
i just tired without the vpn client, and it works like a charme.

ive made this bug at launchpad
[https://bugs.launchpad.net/bugs/195862](https://bugs.launchpad.net/bugs/195862)

if you have any detailed information, feel free to type it in.

but it is kinda hard when the entire machine crashes like that. :(

---

