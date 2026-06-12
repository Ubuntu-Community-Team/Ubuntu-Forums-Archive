---
title: "Lost grahical interface with latest updates"
date: 2014-01-08
forum: General Help
---

### Post by Buntu Bunny on 2014-01-08
Dell Inspiron 700m
Xubuntu 12.04.3 

This morning I checked for updates on this old laptop and installed them. Reboot required, but what came up after that was CLI only. It asked for login and password, which were accepted, but no graphical interface. I need this! How do I get it back?????

ADDITIONAL INFORMATION: after signing in, I get the impression that it has no record of anything. This is what it tells me:

> Ubuntu 12.04.3 LTS buntubunny-Inspiron-700m tty1

Welcome to Ubuntu 12.04.3 LTS (GNU/Linux 3.2.0-58-generic i686)

*Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

The programs included with the Ubuntu system are free software;
the exact distrubution terms for each program are described in the
individual files in /usr/share/doc/*/copyright

Ubuntu comes with ABSOLTUELY NO WARRANTY, to the extent permitted by
applicable law.

The i686 puzzles me; is that a problem since my computer is i386?

---

### Post by Dennis N on 2014-01-08
Hi Buntu Bunny,

You are not alone. Same thing here on my old Dell 6000 laptop, also Xubuntu 12.04.3 two days ago. But, in my case I got no login prompt until I switched to a terminal. After login, the command **startx** (or maybe **sudo startx**) worked to move things along and get to the desktop.

After that, a few more startups show it may or may not get to the desktop normally, it seems. To soon to tell how often this happens.

My other laptop (a few years newer), same distro, same update, is not affected at all.

Sorry I have no real solution.

---

### Post by Buntu Bunny on 2014-01-08
> **Dennis N said:**
> You are not alone. Same thing here on my old Dell 6000 laptop, also Xubuntu 12.04.3 two days ago. But, in my case I got no login prompt until I switched to a terminal. After login, the command **startx** (or maybe **sudo startx**) worked to move things along and get to the desktop.

After that, a few more startups show it may or may not get to the desktop normally, it seems. To soon to tell how often this happens.

My other laptop (a few years newer), same distro, same update, is not affected at all.

Sorry I have no real solution.

```
startx
```
worked!

Thank you so much Dennis N. It may not be a "real" solution, but it got the destop back. Hopefully someone will figure out a more permanent fix soon.

---

### Post by Dennis N on 2014-01-08
I will add that when you want to quit, you may have only the logout option (shutdown grayed out) from the Xubuntu Desktop. You end up back in the terminal, so you run **sudo shutdown now** to turn the computer off. To reboot, use **sudo shutdown -r now**.

---

### Post by Buntu Bunny on 2014-01-08
> **Dennis N said:**
> I will add that when you want to quit, you may have only the logout option (shutdown grayed out) from the Xubuntu Desktop.

I just checked and that is indeed the case.

> **Dennis N said:**
>  You end up back in the terminal, so you run **sudo shutdown now** to turn the computer off. To reboot, use **sudo shutdown -r now**.

Thank you! I've got that jotted down and tucked away in the computer's carrying case. I don't use this little laptop often, but would be lost without it.

---

