---
title: "upgrade a debian package"
date: 2004-12-02
forum: General Help
---

### Post by marcadams on 2004-12-02
Hi;

I am just getting to grips with Linux...
One quick question - if I wanted to upgrade an existing package E.g. Firefox, is it common just to download the new package and run it - or is it necessary to uninstall the existing one first? 

If I install a newer version, does it generally overwrite the existing files on my machine, or will I then have several folders, containing several copies of files?

I suppose I am just after the general etiquette for installing / upgrading packages - before I clutter my newly installed version of Ubuntu!

Many thanks,
Marc

---

### Post by clasqm on 2004-12-02
If you are gpoing to upgrade a .deb you would use

dpkg -i <packagename.deb>

If there is cleaning up to do, dpkg will do it for you

But rather use command-line apt-get or its synaptic frontend. They run dpkg for you, but also check on all other packages on which yours may be dependent., clean up if necessary and install the dependencies. This is the true beauty of running a debian-based setup - there is just no way to get into the whole "conflicting libraries" mess.

Well, there is, but you really have to be trying to mess up your system!

---

### Post by marcadams on 2004-12-03
Thanks for the info.

I've been a Windows software developer for the last ten years, and the debian package system does appear to have a lot of advantages.

Just a follow up on your posting - if wanted to upgrade FireFox, for instance, from 0.9x to the current 1.0 version, what would be the safest method. You mentioned it could be done through the synaptic front end - but how? How do I force synaptic to install version 1.0 instead of it's current offering??

Many thanks
Marc

---

### Post by WW on 2004-12-03
For Firefox 1.0, you could add Markus Hubig's repository and install it from there (using Synaptic or apt-get).  Check out the "BreakMyUbuntu" wiki page for more information: [http://www.ubuntulinux.org/wiki/BreakMyUbuntu](http://www.ubuntulinux.org/wiki/BreakMyUbuntu)

---

