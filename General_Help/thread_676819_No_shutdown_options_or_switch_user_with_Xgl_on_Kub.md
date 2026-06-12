---
title: "No shutdown options or switch user with Xgl on Kubuntu 7.10"
date: 2008-01-24
forum: General Help
---

### Post by kprateek88 on 2008-01-24
I recently installed Kubuntu 7.10 on an Acer Aspire 4720. I had to install Xgl for compiz to work. Now the shutdown menu (K menu -> Logout) has a single option "log out", and no hibernate, suspend, etc. As a workaround, I can suspend and hibernate from guidance-power-manager from the system tray. However, I will like to have the usual shutdown menu. How is this possible? A more serious problem is that there is no switch user option in the K menu or the screen-is-locked dialog box. I don't know of any workaround for this.

I Googled for this and got some old and mostly gnome-centric posts. I never had gnome (and gdm in particular) installed on this system.

Please help.

---

### Post by kuja on 2008-01-24
Do you still use kdm for logging in? Without the login manager KDE won't give you any switch user or logout options. 

If not you might want to set things up so that you can login to your XGL session through kdm. 

If this isn't the case then I don't know what could do it.


One workaround for not having a switch user option - albeit not a terriffic one, would be to switch to a tty and run the command:
[code]xinit -- :1 vt9[/code[

Changing the two numbers to suit, the first is the display number, it starts at 0 and goes up from there, so if you already have one X session going the next will be 1, 2, etc. The next number is the vt#, it starts at 7 and runs thru 12. Default for the first one is 7. I think usplash in ubuntu reserves vt8, so I recommend skipping 8 and going to 9. 

Good luck.

---

### Post by kprateek88 on 2008-01-26
I'm not entirely sure if I'm using kdm, but it seems I am:

1) I installed Kubuntu a few days ago on this system and have not done anything manually to affect whether kdm is used.
2) The login screen is the usual default Kubuntu login screen.
3) ps aux shows "/usr/bin/kdm -config /var/run/kdm/kdmrc" running.

Thanks for the workaround for user switching... ugly, but better than nothing.

---

### Post by kuja on 2008-01-26
Hmm, I wonder if it just doesn't like XGL ... hard to say.

---

### Post by kprateek88 on 2008-02-01
I noticed that the Xgl process is running as my user, not as root. Could this be the problem?

---

### Post by kuja on 2008-02-02
It's hard to say if that is it or not - X is running as root for me ... and if I do recall running the shutdown command requires root privileges ...... so yeah, could be it eh?

---

