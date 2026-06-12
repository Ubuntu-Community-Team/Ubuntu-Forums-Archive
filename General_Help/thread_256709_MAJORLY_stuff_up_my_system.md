---
title: "MAJORLY stuff up my system"
date: 2006-09-13
forum: General Help
---

### Post by mikesena on 2006-09-13
Hi,  I have been trying to install compiz, but in the process managed to stuff it up, getting an x-server graphical error.  ive had this happen before, so i removed the gdm.conf-custom file, and put my backup xconf.conf file (from /etc/X11) overwriting the old.  when it started up, it sitll have that problem.  i so removed a stack of packages to do with compiz, including any x server ones that needed to be installed, i don't know if they were already on my system or not.  this still didn't fix the problem, gdm was complaining about something.  i then removed gdm and installed it, using apt-get, still nothing.  then, i removed the inst.d/gdm file by mistake (didn't know what it did), now i don't have gdm at all.

i can't reformat this computer, i still have data on it!  and a lot of packages, setup files etc.  how can i fix this?  i do have internet, thankyou for saving my conenction linux, i have dapper drake 6.06, i have root access, i have the ubuntu lts 6.06 cd.

please help!

---

### Post by David Corrales on 2006-09-13
First, refer to the tutorial you used to install compiz and do the same steps backwards. That will get your system back to it's original state.
Try reinstalling gdm from synaptic. If it's still misconfigured, run **sudo dpkg-reconfigure gdm**

---

### Post by pravuil on 2006-09-13
You could also install kdm but I'm sure you want your gdm back. Sounds like you need to do this: sudo dpkg-reconfigure xserver-xorg because the main conflict with XGL directly effects xorg more than anything. You might want to do the same for xwindows-system-core just to be safe. Use aptitude and press the "/" key to search for the right packages. Kind of curious, did you install any type of graphics driver previous to installing XGL? If so, did you make sure it worked right before trying to install XGL?

---

### Post by mikesena on 2006-09-13
thankyou both, but especially pravuil because i am now logged in again, but using kdm.  ive tried uninstalling and reinstalling gdm, i got the /etc/init.d/gdm file as well, but it doesn't wokr, it just loads the concolse instead, i presume there's an error.  what should i do to get gdm again?

---

