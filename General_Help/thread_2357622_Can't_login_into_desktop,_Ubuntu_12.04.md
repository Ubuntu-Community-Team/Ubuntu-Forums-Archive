---
title: "Can't login into desktop, Ubuntu 12.04"
date: 2017-04-04
forum: General Help
---

### Post by msousa on 2017-04-04
Hi

When booting my laptop wit Ubuntu 12.04, I can see my desktop background but the login prompt keeps looping back around and asking me to login again. I've tried many of the solutions recommended on this forum like deleting .Xauthorixation, doing chown on my home directory, reinstalling/reconfiguring lightdm, etc. Anything else I might try?

Thanks...
[COLOR=#333333][FONT=UbuntuRegular][/FONT][/COLOR]

---

### Post by TheFu on 2017-04-04
Support for 12.04 ends in less than 30 days. [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) April 28 is the end for that release.

Move to a newer release.  Troubleshooting this isn't worth the time anymore (and hasn't been since about last June, IMHO).

Boot off alternate media, backup any files you need to keep and install 16.04. If that doesn't go, try 14.04. If neither work easily, go back to 16.04 and get help on that release being installed.

---

### Post by Impavidus on 2017-04-04
Most likely some invalid configuration or a permission issue that causes the desktop environment to fail to start, but you already tried the most common causes.

What about the nuclear option? Support for 12.04 LTS is running out in a few weeks. Copy your documents, bookmarks, email to a backup drive, wipe the hard drive and install 16.04 LTS (first check for compatibility with your hardware). Don't keep your config files. Four years is a long time, software has changed and your old config files may not be relevant any more.

---

### Post by msousa on 2017-04-04
Thanks for the replies TheFu and Impavidus. I tried updating to 14.04 awhile ago, but unfortunately my laptop is quite too old and the update said it could not continue. If I remember correctly, it complained most about the graphics card in my laptop. So I stayed with 12.04 up until now. I will keep looking into this until I pick up some newer hardware, thanks...

---

### Post by RobGoss on 2017-04-04
Try upgrading by doing a fresh installation and see how that goes. I would run the live installer first that should give you a good idea of how things will perform

---

### Post by TheFu on 2017-04-04
Try Lubuntu 16.04 for old laptops.  If the GPU isn't recognized, you can always select the VESA mode.  Open a new thread for help getting it installed. Make the title the exact laptop make model with "install."

Don't try an upgrade - do a fresh install. Be certain to backup any files you cannot lose first.

Running an OS unpatched is really bad, unless it doesn't have any network connection.

---

