---
title: "run command during boot"
date: 2005-09-20
forum: General Help
---

### Post by A-star on 2005-09-20
Hi all,

I installed ipac-ng to monitor how much I download and upload on my machine.
The problem is everytime that I reboot I have to run this command by "fetchipac -S".

Is there anyway that this can be done automatically?

Kind regards
A-star

---

### Post by KingBahamut on 2005-09-20
Administration > Preferences > Session 

Youll find a session startup tab, just go in there and add the commands you need at startup.

---

### Post by A-star on 2005-09-20
[QUOTE=KingBahamut]Administration > Preferences > Session 

Youll find a session startup tab, just go in there and add the commands you need at startup.[/QUOTE]

Thanks for the help

---

### Post by A-star on 2005-09-21
[QUOTE=KingBahamut]Administration > Preferences > Session 

Youll find a session startup tab, just go in there and add the commands you need at startup.[/QUOTE]
 Is there also another way to do this?
I want it to run it on a machine that has nu gui available.

---

### Post by fordfan753 on 2005-09-22
[QUOTE=A-star]Is there also another way to do this?
I want it to run it on a machine that has nu gui available.[/QUOTE]

You could write a short init script and get it to load last at boot...

---

### Post by A-star on 2005-09-22
[QUOTE=fordfan753]You could write a short init script and get it to load last at boot...[/QUOTE]
 I have found a solution to do it,
I added the command to "/etc/init.d/bootmisc.sh"
And it starts up nicely now.

Thanks for the help.

---

### Post by A-star on 2005-09-23
[QUOTE=A-star]I have found a solution to do it,
I added the command to "/etc/init.d/bootmisc.sh"
And it starts up nicely now.

Thanks for the help.[/QUOTE]
Boy what was I wrong, this didn't help at all.
can anyone help me to write an init script?

Kind regards
A-star

---

### Post by garlito on 2005-09-23
> Boy what was I wrong, this didn't help at all.
can anyone help me to write an init script?

I think a shell script named S80ipac-ng and placed in /etc/rcS.d should work. Inside simply put:

fetchipac -S

If you want to be able to stop, restart and so on, you must add code to manage that. You can see samples at /etc/init.d

Bye

---

