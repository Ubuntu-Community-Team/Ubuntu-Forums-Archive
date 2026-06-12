---
title: "Starting Services Automatically?"
date: 2005-05-07
forum: General Help
---

### Post by akinwale on 2005-05-07
Hello,
I have tried to setup Apache to start automatically when my system boots by copying the apachectl file to init.d, and then creating symbolic links in the required runlevels.

I did this on Slackware, and it worked, but I just can't seem to figure out how to get it to work on Ubuntu. I guess this will apply to other automatic startup scripts as well...

Any solutions?

Thanks.

---

### Post by Xerampelinae on 2005-05-07
Maybe you're looking for the update-rc.d command.  (man update-rc.d)

Basically,

update-rc.d apache defaults


However, your manual way should work too.  There should be an apache startup script in /etc/init.d/, and then you create links to that in /etc/rcX.d of the form /etc/rcX.d/S50apache. (man init)

EDIT: Oops, I'm not so familiar with apache, but is the apache control file an init script?  It should have start, stop, and restart cases and look similar (at a high level) to the other init scripts... it could be your problem. (I would think if you installed apache via apt-get, it would put something in /etc/init.d by default though)

---

