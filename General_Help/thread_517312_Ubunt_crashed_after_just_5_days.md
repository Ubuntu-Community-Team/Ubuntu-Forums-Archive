---
title: "Ubunt crashed after just 5 days"
date: 2007-08-04
forum: General Help
---

### Post by azad on 2007-08-04
Hey guys. I've been using Ubuntu Fiesty for a few days and this is my favourite distro ever. 

Today I decided to try installing LAMP on my machine and I used apt-get to get the files. The download was half  done and all of a sudden, the screen went black and then I saw the splash screen. It asked for a username and password. After logging in there was an error screen that said:

```
/etc/gdm/PreSession/Default : Registering in your session with wtmp and utmp
/etc/gdm/PreSession/Default : running : /usr/X11R6/bin/sessreg -a .......
etc/gdm/Xsession : Beginning default session
SESSIO MANAGER = local/master : /tmp/ICE-UNIX/5369

Initializing Gnome-mount extension

*** glibc detected *** x-session manager : malloc(); memory corruption(fast) : 0x08251fao ***
```

When I click OK, the screen goes black again and the whole thing happens again. I tried rebooting the machine but it keeps happening.

I recently changed my boot screen and tried to Install WinXP with VirtualBox when it froze and I had to push the reset button. Maybe that has something to do with it.

Little help, please? Thanks in advance.

---

### Post by chewearn on 2007-08-04
Just a guess. it could be a hardware problem.  If your computer is not spanking new, try clean out the interior a bit.  Sometimes, dust or corrosion caused problem in the memory modules metal contacts after extensive use.  Maybe unplug and plug back the modules a few times, then run memtest from the livecd.

---

