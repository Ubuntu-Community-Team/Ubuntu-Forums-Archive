---
title: "Does ubuntu have inittab?"
date: 2007-02-07
forum: General Help
---

### Post by sdbolts21 on 2007-02-07
Hi all,

I am a ubuntu noob.  Does ubuntu have a replacement for inittab?  Does it have the ablity to change Run levels?

Thanks,

---

### Post by llamakc on 2007-02-07
What runlevel do you want to change to?

In Edgy (which uses Upstart) /etc/inittab does not exist, but you can look in /etc/event.d for the tty entries, and the rc-default script that calls runlevel 2 as default.

---

### Post by jomiz80 on 2007-03-20
I'm trying to install [Monica]("http://www.pcbypaul.com/software/monica.html") to calibrate my monitor, and I get an error when I try to start the program that says:

> Monica cannot read your /etc/inittab file...

This is used by Monica to determine your login type, graphical or text-based. If unknown, then Monica will assume a non-graphical log in and place the call to monicar into the .xinitrc file in your home directory.

Could anyone give me some clarification what the /etc/inittab does, and what this means. I'd like to get this program so that I can calibrate my monitor. Any suggestions?

---

