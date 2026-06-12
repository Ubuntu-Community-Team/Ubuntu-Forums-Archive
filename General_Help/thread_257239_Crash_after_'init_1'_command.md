---
title: "Crash after 'init 1' command"
date: 2006-09-14
forum: General Help
---

### Post by rutgerw on 2006-09-14
If I start my ubuntu box in multi-user mode, and want to change later to single user mode using 'init 1' my computer crashes.

I haven't found any entries in the logs. I'm using AMD64 release.

Does anyone have a clue?

---

### Post by Ramses de Norre on 2006-09-14
On which point does it crash? While going out of runlevel 2 or while going into runlevel 1?
What are the messages you got on screen before it crashed?

---

### Post by rutgerw on 2006-09-14
It crashes at the point when the 'sending all processes the Term signal' appears on the screen.

---

### Post by rutgerw on 2006-09-21
Doesn't anyone have an idea on this one?? Please?

---

### Post by mssever on 2006-09-21
I don't know if this will help, but I use the command telinit 1. I guess you should hunt through the logs in /var/log and see if there are any error mesages there.

What kind of crash are ou talking about? A complete lockup?

---

### Post by rutgerw on 2006-09-22
Telinit 1 does exactly the same. The problem is, there don't seem to be any relevant entries in the logs. 

Indeed, my computer locks yp completely. It will only respond when I press the power button. :confused:  All in all I find this a rather strange problem.

---

### Post by mssever on 2006-09-22
I have no idea what the problem is... Can you boot in recovery mode? What about manually switching between various other runlevels?

I recently learned a slightly nicer way to hard reboot (I think I'm remembering these correctly):

Alt+SysRq+S (SysRq is the same as print screen--this syncs the discs)
Alt+SysRq+U (remounts filesystem read-only)
Alt+SysRq+B (reboot)

---

### Post by rutgerw on 2006-09-22
I can boot up in recovery mode (btw runlevel switching in recovery mode seems to work fine!). Switching to other runlevels also doesn't provide any problems. Probably since these are configured the same as runlevel 2. I'm hoping these keyboard shortcuts will help as my pc is totally irresponsive.

---

