---
title: "terminal server client win xp desktop sharing"
date: 2005-05-26
forum: General Help
---

### Post by knathraak on 2005-05-26
Hi, I'm trying to use the terminal server client to share a desktop on a windows xp (professional) machine.  I can connect and log in, but it locks the desktop on the host machine.  I need the desktop on the host machine to remain interactive, so I the user (my parents) can see what i'm doing/clicking on, etc.

Btw, i've tried vnc, and that's what we're currently using.  it works okay, but I'd like to give windows remote desktop a try to see if I like it any better.

Thanks in advance for the help
Zach

---

### Post by TripHammer on 2005-05-27
Hi,

This cannot be done on Windows XP by design.  When using MS RDP (terminal services) you can only shadow other people's **remote** sessions.  TS is not for desktop sharing.

---

### Post by Takis on 2005-05-27
So what you're really after is something like Remote Assistance?

---

### Post by knathraak on 2005-05-27
[QUOTE=Takis]So what you're really after is something like Remote Assistance?[/QUOTE]

I guess so.  I hadn't really realized there was a difference between windows xp's remote desktop & remote assistance?  Is there a way to use the ts client with xp's remote assistance?  I know on the xp host, there are settings to allow remote assistance "offers" without requiring "invitation".

Is there anyway to accomplish this other than VNC?

Again, it's not that there's a specific problem with VNC, I would just like to try what's built in to windows, particularly to take advantage of windows' own authentication.

Thanks for the help

---

### Post by Takis on 2005-05-28
I honestly don't know the answer to this one, I only ever use the TS desktop. I'd be interested if there is something that can be used, though.

---

