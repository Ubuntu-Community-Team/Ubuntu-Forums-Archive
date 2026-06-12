---
title: "permissions help - running an driver installer script"
date: 2018-10-05
forum: General Help
---

### Post by kurt18947 on 2018-10-05
Maybe my search skills are lacking but I can't find releveant help. I'm trying to install Samsung printer and scanner drivers, Samsung - now HP - supply Univeral Linux Drivers (ULD). The destination is a fresh install of Xubuntu 18.04.1 64 bit. I've been using these for a few years and have gotten the scripts to run until recently. My source is here:

```
https://support.hp.com/us-en/drivers/selfservice/samsung-xpress-sl-m2070-laser-multifunction-printer-series/16450377
```

My machine is an M2870 but there is one script for all similar machines. The script is in a folder on the desktop of the user with administrator privileges. I did set install-scanner.sh to be executable. I tried what appears to be the commonly recommended procedure first and got this:

                        ```
firstfloor@firstfloor-desktop:~/Desktop/Samsung$ ./install-scanner.sh

 **** Root privileges are required
  
```

Root privileges are required? O.K. so  tried this:

```
firstfloor@firstfloor-desktop:~/Desktop/Samsung$ sudo ./install-scanner.sh

 [sudo] password for firstfloor:  
 **** Running install ...

 **** Press 'Enter' to continue or 'q' and then 'Enter' to quit. :  


**** Do you agree ? [y/n] : y
 ./noarch/package_install.sh: 46: ./noarch/package_install.sh: ./noarch/package_install.sh: Permission denied
 **** Install finished.


```

I tried using bash as well 

```
sudo bash install-scanner.sh

```
but with the same result - permission denied. What am I doing wrong?  Thanks for any help on what seems like a simple straight forward procedure.

---

### Post by JengaBlocks on 2018-10-05
Maybe a folder and file permission problem. Change ownership.

---

### Post by oldos2er on 2018-10-05
I would try opening a root terminal with ```
sudo -i
``` and running the script from there.

---

### Post by kurt18947 on 2018-10-06
> **oldos2er said:**
> I would try opening a root terminal with ```
sudo -i
``` and running the script from there.
I'm pretty gunshy about using root. I'll do some reading on how to not trash my system.

---

### Post by kurt18947 on 2018-10-06
> **JengaBlocks said:**
> Maybe a folder and file permission problem. Change ownership.
I thought that running from an admin account permissions wouldn't matter. I'll look at the ownership and permissions again. Thanks for your help.

---

### Post by steeldriver on 2018-10-06
How did you extract the archive? perhaps the executable permissions on the ./noarch/package_install.sh file got lost? Check with

```

ls -l ./noarch/package_install.sh

```
or
```

namei -l ./noarch/package_install.sh

```

---

### Post by kurt18947 on 2018-10-06
Thanks to all for their input. I've used Ubuntu Gnome since Gnome 2 went away but had SWMBO using Xubuntu because their UI seemed more stable, SWMBO does NOT like change as she will proclaim to one and all. Since mainline Ubuntu has gone back to Gnome I'm hoping the UI will be stable. So I overwrote the Xubuntu install with Ubuntu and the script ran as expected and both printer & scanner work. What was the difference re permissions between Ubuntu 18.04.1 and Xubuntu 18.04.1? Dunno but there seemed to be one. I can set Ubuntu up with the help of a couple extensions to look and work much like her Xubuntu desktop.

---

