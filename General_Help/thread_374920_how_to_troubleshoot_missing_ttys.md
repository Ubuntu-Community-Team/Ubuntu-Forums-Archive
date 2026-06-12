---
title: "how to troubleshoot missing ttys"
date: 2007-03-03
forum: General Help
---

### Post by Sencer on 2007-03-03
I am running edgy (upgrade from dapper) and recently noticed that all my ttys are missing. When I hit ctrl-alt-F[1-6] I only get a blinking cursor, but no login prompt.

I've checked inittab, then found out that things have moved to event.d/ttyx in edgy. But everthing looks ok there. Nothing commented out or renamed. 
grub/menu.lst has this vga=791 and my graphics card is an intel i195.

I couldn't find anything that looked relevant in syslog.

ps aux shows the processes to be running:

> 
root      3932  0.0  0.0   1600   416 tty1     Ss+  Mar02   0:00 /sbin/getty 38400 tty1
root      3933  0.0  0.0   1600   412 tty2     Ss+  Mar02   0:00 /sbin/getty 38400 tty2
root      3934  0.0  0.0   1596   416 tty3     Ss+  Mar02   0:00 /sbin/getty 38400 tty3
root      3935  0.0  0.0   1596   416 tty4     Ss+  Mar02   0:00 /sbin/getty 38400 tty4
root      3936  0.0  0.0   1596   416 tty5     Ss+  Mar02   0:00 /sbin/getty 38400 tty5
root      3937  0.0  0.0   1600   416 tty6     Ss+  Mar02   0:00 /sbin/getty 38400 tty6


Any suggestions on how I can proceed to get my ttys back?

---

### Post by addisor on 2007-03-04
Any Joy, in the same situation???

---

### Post by Sencer on 2007-03-05
No, not yet. I am starting to think it might be connected to the upgrade to Edgy. I remember that before the upgrade I used to see a few messages about the kernel/pci somethig before usplash started - and I remember thinking "hey, they finally cleaned that up" after the edgy upgrade. Now I think that that's the point at which my ttys went missing (and with them the messages).

No idea for a solution yet. I'll try to search the bugs/fixes since edgy's release...

---

