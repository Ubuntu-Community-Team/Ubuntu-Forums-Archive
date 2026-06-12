---
title: "[SOLVED] Log in problem (Kubuntu Feisty)"
date: 2007-10-23
forum: General Help
---

### Post by merinette on 2007-10-23
I've been running Kubuntu on my Thinkpad for about a year now, and for no discernable reason, suddenly I cannot log in as user. That is, I can input username & password on the splash screen, & it is accepted, but rather than showing the "Starting KDE..." screen, the display goes black except for the cursor... & then the splash screen is displayed again. 

I can, however, log in as 'root', from the splash screen or startx from recovery mode, and everything is fine. 

This is the extent of my troubleshooting, I guess:  

After I logged in @ root and loaded desktop, used 'System Settings' GUI to create new user, which I also cannot log on as(same deal as old user). 

```
root@twylo:~# ls -ld /home/merinette
drwxr-xr-x 60 merinette merinette 4096 2007-10-23 19:36 /home/merinette
root@twylo:~# su merinette
merinette@twylo:/root$

```

Can anyone help me figure out what went wrong, & how to log in as user again? (Obviously I'm still a pretty big noob, so you might have to take it slow -- sorry...)

---

### Post by merinette on 2007-10-23
Reinstalled KDM with apt-get. All better.

---

