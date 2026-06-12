---
title: "exsession errors, low disk space?"
date: 2007-09-04
forum: General Help
---

### Post by Perfex on 2007-09-04
I was downloading a debian iso file about 4 gigs, working with gimp, surfing. system was getting really slow, so I restarted.

When the computer booted back up and into ubuntu.. I get the message:

Your session only lasted less than 10 seconds. if you
have not logged out yourself, this could mean that
there is some installation problem or that you may be
out of diskspace. Try logging in with one of the failsafe
sessions to see if you can fix the problem.

View details (~/.xsession-errors-file)

/etc/gdm/PreSession/Default: Registering you session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u  /var/run/utmp -x  "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "robert"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/ubuntu:/tmp/.ICE-unix/4943


I logged into the terminal executed the following commands
sudo apt-get clean
sudo rm -R /var/cache/apt/archives

They did not work, I have diskspace some 22 gigs of it.

Can anyone enlighten me on the problem I am having :confused:

Thank you in advance :)

---

