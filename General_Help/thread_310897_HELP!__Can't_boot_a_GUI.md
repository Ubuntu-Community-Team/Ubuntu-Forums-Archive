---
title: "HELP!  Can't boot a GUI"
date: 2006-12-02
forum: General Help
---

### Post by fatalfuj on 2006-12-02
I've tried Linux a few times (Redhat, Xandros) but Ubuntu is the first one I've fallen for.  I love it.  The fact that it supports my Game Theater XP (old, strange soundcard) right out of the box blew me away.. yay ALSA!!

I'm running **Kubuntu** and I'm in trouble.  After attempting to install Beryl and rebooting, I'm thrown into a command line, every time.  How I can boot into X or anything but a command line?  I recently did a fresh install to 6.10 and I can't afford to lose what data I've got. 

Please help. I can login to the CLI but don't know the next step from there.  I'm in XP now and hating every minute of it. :/

---

### Post by ciscosurfer on 2006-12-02
Login and then type **startx**

---

### Post by fatalfuj on 2006-12-02
I knew it was something as simple, and this joint is in your name if this works, THANKS!!!

---

### Post by blackmh on 2006-12-02
Go to /etc/X11 folder and see if backup of xorg.conf exist. I hope you backed it up before you installed beryl. If there is backup simply type sudo nano nameofbackup and save it as xorg.conf. Should do the job...

---

### Post by fatalfuj on 2006-12-02
Thanks for the reply, making a little progress!

startx gives me this error:

'fatal server error, requested entity already in use
 x10: fatal IO error 104'

I tried 'startkde' and it spits back even crazier lines.  

blackmh: going to try your advice next, I was sorta drunk when trying to install Beryl, so I hope the guide called to backup my xorg.conf, otherwise am I screwed?

I really appreciate the quick responses. :)

---

### Post by ciscosurfer on 2006-12-02
Reboot your machine and try the startx command again.  If it doesn't work, switch ttys (CTRL-ALT-F2 through F6 for other terminal lines...F7 will bring you back to where you were...at least it does when you're in a GUI)

---

### Post by fatalfuj on 2006-12-02
Back in Kubuntu!!!  Logged in to follow up.

First of, the willingness of people that wanna help is truly outstanding.  I plan on giving back what I know too.  :)  I only use Linux for one program.. Amarok (and Krusader because I was addicted to Total Commander).. and I'm thinking about installing Gnome, is there ANY actual performance difference running KDE apps in Gnome?  I'm running P4 2.2 with 756mb ram.  Should I just stick with KDE?  

I ask because I had near to no idea how big the Ubuntu community is, and with most people running Gnome, something must be right, right?  

Anyone else having similar trouble to me (I always search first) I reverted to the first xorg.conf, then command 'startx' and reinstalled nvidia drivers, somehow there was 5+ backups sitting there nicely.  :)

---

### Post by ciscosurfer on 2006-12-02
Glad you're back up and running.

The KDE vs GNOME debate is really a matter of preference, when it all boils down.  I use many KDE apps in GNOME, but prefer GNOME as my main environment.

If you like KDE, then stick with it and just run GNOME apps on top of it.  KDE apps will always run a bit quicker in a native KDE environment...likewise, with GNOME apps in GNOME.

---

