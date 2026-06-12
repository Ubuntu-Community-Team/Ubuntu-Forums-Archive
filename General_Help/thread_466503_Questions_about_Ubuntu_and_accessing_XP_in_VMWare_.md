---
title: "Questions about Ubuntu and accessing XP in VMWare Guest"
date: 2007-06-06
forum: General Help
---

### Post by web1b on 2007-06-06
Is there any way to setup VMWare and a guest OS to automatically launch when the computer is powered on?

We would like create XP virtual machines in Ubuntu workstations, but we do not want to confuse the users with dealing with Ubuntu.  We also need the Ubuntu desktop completely locked down to prevent "curious" users from playing around with with Ubuntu host workstation or accidentally exiting VMware and becoming confused as to how to get back to their XP guest.  We need them to see as little of the host OS as possible so it seems to them almost like they are logging directly into an XP box.

We would like the users to be able to just power on the machines, not be prompted for any Ubuntu Linux login information, and have WMWare and the XP guest automatically launch so all they see is the XP login screen.

Can this be done at all?  If so, how?

---

### Post by kidders on 2007-06-08
Hi there,

I can't help wondering why you would want to do this. It seems odd to deliberately penalise a box's primary OS by virtualising it, to say nothing of the security implications of forcing Linux not to authenticate users. You'd essentially be taking a slow, insecure OS, making it even slower and even less secure ... and adding vmware's glitches & hardware management issues on top.

If you really do want to habitually run one OS within another, would suggest not bothering to load a display manager at all, rather than trying to hide desktops, etc. That would probably be the most sensible approach.

[SIZE="1"][COLOR="Silver"][UAResolved][/COLOR][/SIZE]

---

