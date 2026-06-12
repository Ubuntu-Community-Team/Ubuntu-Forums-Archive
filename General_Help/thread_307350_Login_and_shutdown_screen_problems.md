---
title: "Login and shutdown screen problems"
date: 2006-11-26
forum: General Help
---

### Post by arnold0 on 2006-11-26
Hi, my problem is that the other day all of a sudden my nice ubuntu login screen changed to this ugly blue screen with a flower in the corner. This happened soon after I started using beryl, although it may not be related.

I have tried to change it back through system>administration>login screen
but when I try to open that it just pops something up that says "starting administrative app" and then it closes. I have tried opening it in terminal with  sudo gdm setup but I get this

 Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.
Could not access GDM configuration file.

I have also tried these commands 
sudo aptitude reinstall usplash-theme-ubuntu
and
sudo aptitude reinstall usplash-theme-ubuntu

I have also tried turning off beryl and emerald in startup options still no luck.


Also, in my shutdown options I have no restart and shutdown buttons.

---

### Post by arnold0 on 2006-11-26
bump

---

### Post by phixom on 2007-01-23
I've exactly the same problem.
Also after login in the ugly GDM I've no shutdown and reboot buttons in the GDM-logut window.
If I've logged in on Console (VT1-6) and restarted GDM and everything works. GDM has the correct theme and the logout/restart buttons are existing.

It looks like a permission/corect user rights error in the startup script.

Is there someting solution?

phixom

---

