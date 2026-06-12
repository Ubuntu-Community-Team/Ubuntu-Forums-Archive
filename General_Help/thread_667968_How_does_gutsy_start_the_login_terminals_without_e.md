---
title: "How does gutsy start the login terminals without /etc/inittab?"
date: 2008-01-14
forum: General Help
---

### Post by rocketman768 on 2008-01-14
So, since there is no /etc/inittab anymore, I am wondering exactly how gutsy starts the tty terminals (you know...ctrl-alt-f1, ctrl-alt-f2,...). Problem is I have a very small gutsy installation from scratch that ends after saying "executing rc.local" and just sits there without starting the consoles. I know it has to do with /etc/events.d/* . All that stuff is there including the files tty1 tty2 ... tty6.

Anyone?

---

### Post by rocketman768 on 2008-01-16
Help please :(

---

### Post by p_quarles on 2008-01-16
They're stored as individual files in /etc/event.d .

---

### Post by rocketman768 on 2008-01-16
I know that. Like I said, /etc/events.d/tty1 is there.

---

### Post by p_quarles on 2008-01-16
I guess I'm not sure what you're asking, then. Do you want to disable some of the ttys? Or is it the fact that they're not starting? Does the X server itself start up?

---

### Post by pointone on 2008-01-16
Have you tried hitting enter? Sometimes, the terminal will start before the boot is fully completed and later boot messages will scroll the login prompt off screen. Hitting enter will bring back the prompt.

Also, is this problem affecting all terminals (1 through 6) or just tty1?

---

### Post by rocketman768 on 2008-01-16
Yeah, I've tried hitting enter, and it is indeed affecting tty1-6. I put "/sbin/getty 38400 tty1" in the rc.local and it started up just fine, but I would like to figure out why the tty1-6 scripts in /etc/events.d/ is not starting correctly.

---

### Post by galileon on 2008-05-18
same problem here. any ideas?

cheers

---

