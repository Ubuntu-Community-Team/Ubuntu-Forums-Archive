---
title: "[SOLVED] Downloaded Bad Nvidia Driver"
date: 2008-07-02
forum: General Help
---

### Post by CodyT07 on 2008-07-02
Here is the error before I get to the story

"This is a pre-release version of the X server from The X.Org Foundation
It is not supported in any way
Bugs may be filled in the bugzilla at [http://bugs.freenode.org/](http://bugs.freenode.org/).
Select the "xorg" product for the bugs you find in this release. 
Before reporting bugs in pre-release versions please check the latest versions in the X.Org Foundation fit repository. 
See [http://wiki.x.org/wiki/Gitpage](http://wiki.x.org/wiki/Gitpage) fir git access instructions.

X.org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build operating system: Linux Ubuntu (xorg-server
2:1.4.1~git20080131-1ubuntu9.2)
Current operating system: Linux cody-desktop 2.6.24-19-generic #` SMP Wed Jun 18 14:43:41 UTC 2008 i686
Build Date: 13 June 2008 01:08:21 AM
-skip a few wiki lines-

Error: API mismatch: The Nvidia kernal module has version 173.14.05, but this Nvidia Driver component has version 169.12. Please make sure the kernal module and all Nvidia Driver components have the same version, 
(EE) NVIDA (0) that there is a support Nvidia GPU in this system and the that the nvidia device files have been created properly. 
Please consulot the nvidia readme for details
Aborting
Screens found but none have a usable configuration.

Fatal server error:
no screens found"

Now the story
I installed ubuntu the way i like, I downloaded and used envy to install my nvidia drivers. A week later I look in my restricted drivers and notice the nvidia one isnt in use (but i still got desktop effects) so I enabled it and when I rebooted I get that error above

Ubuntu - Hardy with ubuntu studio effects
GPU - Nvidia 8500GT

How do I reset ubuntu to a state with out the driver i accidentally installed (e.g system restore)

Sorry if it is the wrong forum and i put the wrong prefix.

---

### Post by sdennie on 2008-07-02
It looks like you are using the kernel module from envyng but the libraries from nvidia-glx-new.  You should probably be able to just re-install the driver with envyng.

---

### Post by CodyT07 on 2008-07-02
> **vor said:**
> It looks like you are using the kernel module from envyng but the libraries from nvidia-glx-new.  You should probably be able to just re-install the driver with envyng.
How so? I cannot access the desktop.

---

### Post by sdennie on 2008-07-02
There is a text based version of envyng.  Hit Ctrl-Alt-F1, login and try:

```

envyng -t

```

You may need a network connection for it to work right.  If so, try to comment out the line in /etc/X11/xorg.conf that looks like this (so, put a # in front of it):

```

   Driver "nvidia"

```

Then do;

```

sudo /etc/init.d/gdm restart

```

That should at least let you login under low resolution and use network manager to connect to your network.

Hope that helps.

---

### Post by forger on 2008-07-02
try:
> 
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm restart


You'll have to reinstall your drivers for nvidia though, using envy:
> sudo apt-get install envyng-gtk
Applications > System tools > Envy NG

---

### Post by CodyT07 on 2008-07-02
I am having a problem with my password not working. 

I am using the right password but it keeps saying login incorrect.


Whops, didnt know it was asking for a login name, my bad

---

### Post by CodyT07 on 2008-07-02
> **vor said:**
> There is a text based version of envyng.  Hit Ctrl-Alt-F1, login and try:

```

envyng -t

```

You may need a network connection for it to work right.  If so, try to comment out the line in /etc/X11/xorg.conf that looks like this (so, put a # in front of it):

```

   Driver "nvidia"

```

Then do;

```

sudo /etc/init.d/gdm restart

```

That should at least let you login under low resolution and use network manager to connect to your network.

Hope that helps.

I type envyng -t and it comes up with
Install nvidia
uninstall
Restart Xserver (+ ati functions)

uninstall the reinstall the driver?

---

### Post by sdennie on 2008-07-02
I don't use envyng so I'm not sure.  It may be safest to uninstall and then reinstall.

---

### Post by CodyT07 on 2008-07-02
Thanks guys, got my desktop back.

---

