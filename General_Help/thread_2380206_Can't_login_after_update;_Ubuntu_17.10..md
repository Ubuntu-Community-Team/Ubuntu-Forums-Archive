---
title: "Can't login after update; Ubuntu 17.10."
date: 2017-12-14
forum: General Help
---

### Post by STPitcher on 2017-12-14
Ubuntu 17.10. 
Update yesterday.  It asked to reboot this morning.  
After reboot, I can't login to my normal user account.  It accepts the password.  Goes briefly to a black screen, and then returns to the login screen.
I have to imagine something somewhere is failing.  Perhaps its leaving a message in some log file?  Where do I look??
I have a temporary account which I can log in to.  Thank goodness!

---

### Post by stepheny on 2017-12-14
Try this:

After you swich on press Ctrl + Alt + F1 to F8 to log into a TTY

Then run:> sudo dpkg-reconfigure gdm and select gdm and reboot

---

### Post by STPitcher on 2017-12-14
Discovered one interesting tidbit.

Ctrl-Alt-F4, still can't login to my own account.  Can only log in to the temporary account.  Same error.  It doesn't report any problem... just drops me back to the login prompt.  It does display a message.. but it disappears immediately.  Looks like a simply login message.

gdm.  Its not installed.  Nor can I install it by either apt-get or dpkg.

- stp

---

### Post by STPitcher on 2017-12-14
Got it!!  Mea Culpa!!

I'd put something bad in my .bashrc.  It was failing.

Really sad that this fails with no hint as to what's wrong.  Hard to diagnose this.

Thanks for your input.

- stp

---

