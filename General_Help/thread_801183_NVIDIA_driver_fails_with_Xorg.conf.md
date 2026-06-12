---
title: "NVIDIA driver fails with Xorg.conf"
date: 2008-05-20
forum: General Help
---

### Post by Zoja on 2008-05-20
I had problem with the latest release of Ubuntu -> 8.04 , it started to freeze out of itself on random moments , shuting down the keyboard and mouse responses. 

so i tried to switch to kubuntu with KDE4

but to my amusement it started happening as well on the kubuntu distro , so i figured it could be the X's , and i installed the latest NVIDIA driver for my GeForce7600GT , the installation automatically created it's own xorg.conf file , then i wanted to startx and recieved a message like this one :

```
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue May 20 18:46:52 2008
(==) Using config file: "/etc/X11/xorg.conf"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) Module "ramdac" already built-in
Error: API mismatch: the NVIDIA kernel module has version 71.86.04,
but this NVIDIA driver component has version 169.12.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
giving up.
xinit:  Connection reset by peer (errno 104):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
```

so i just started with the backup xorg.conf , so to start anything at all , but that probably makes the driver installation useless 

please help

---

### Post by phidia on 2008-05-20
From the error message you provided it seems you have a driver version mismatch. You can use the package manager to see what you have installed and uninstall the conflicting version.
Also see the guide [here]("http://ubuntuforums.org/showthread.php?t=301499") for installing the nvidia driver. Hope that helps.

---

### Post by jimv on 2008-05-20
I had an issue like this awhile ago with my desktop that has the same video card. 

Try this:

```
sudo apt-get remove nvidia-*
```

That will get rid of all your nvidia drivers.  Then do this:

```
sudo apt-get install nvidia-glx-new

```
Then reboot.

Ideally, you should get to the desktop and be able to enable the nvidia driver in the restricted drivers manager.

---

### Post by shifty_powers on 2008-05-20
or just use envy...

```
sudo apt-get install envyng-gtk
```

---

### Post by Zoja on 2008-05-24
envyy kinda sucked 'cause it messed up my X's for good , thx for the help though

---

