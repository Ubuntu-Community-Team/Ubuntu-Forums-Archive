---
title: "Boot Error: &quot;OAFIID:GNOME_ShowDestopApplet&quot; w Ubuntu 10.04.4"
date: 2013-07-13
forum: General Help
---

### Post by flaopa on 2013-07-13
Running Ubuntu 10.04.4 (or 10.04.3 conflicting evidence which), a boot message arose as follows:

 **The panel encountered a problem while load "OAFIID:GNOME_ShowDestopApplet" ** 

 **Do you want to delete the applet from your configuration? ** 

Its repeated occurrence led me to choose 'Delete'.

The result is the Bottom Panel contained only *Trash* & *'Workspace Switches*' The *Show Desktop* and "Application Icons" are not there.

I ran Update Manager for first time in more than six months. As command line text flew by, I saw ... **Ubuntu 10.04.3** (in many lines).

**The missing Bottom Tray features remained.**

Ubuntu & GNOME Versions:

 System Monitor w System Tab
Ubuntu  
Release 10.04 (lucid)
Kernel 2.6.32-49-generic
GNOME 2.30.2
..........................................................
I tried the CLI
**~$ gnome-about --gnome-version**
Version: 2.30.2
Distributor: Ubuntu
Build Date: 06/25/2010
**~$ uname -a**
Linux null01 2.6.32-49-generic #111-Ubuntu SMP Thu Jun 20 22:28:34 UTC 2013 x86_64 GNU/Linux
**~$ cat /etc/lsb-release**
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"
{despite appearance of 10.04.3 during many update command lines scrolling by}

I hope there is some APT_GET-like path, something simpler than reinstalling Ubuntu.

---

### Post by claracc on 2013-07-14
Ubuntu 10.04 has reached its end of life support, so for this reasons, the repositories to update has been moved. For this reason you cannot update nor install software from them.

I recommend you to move to a supported release as 12.04, 12.10 or 13.04.

Anycase, you can still use the moved repositories, following the steps in this link: [http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release](http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release)

---

