---
title: "LightDM fails to log in"
date: 2016-08-31
forum: General Help
---

### Post by CrunchaliciousCaptain on 2016-08-31
I recently lost my main computer and am trying to set up an HP Envy 15 L6F68AV laptop up as a temporary replacement.  For my work I need to use Nvidia's drivers and tools.  After installing the drivers 64bit drivers from Nvidia's website, LightDM fails to log me in.  It's similar to the problem described here:

[http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop](http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop)

However, those solutions don't work for me.  I am already the owner of .Xauthority and /tmp has full permissions.  Reinstalling lightDM was not effective.  Attempting to use GDM just borked my whole system.  .xsession-errors gives this log:
```

openConnection: connect: No such file or directory
cannot connect to brltty at :0
upstart: gnome-session (Unity) main process (6247) terminated with status 1
{The rest of the log just lists a series of processes killed by TERM signal.  I can reproduce the full log if necessary.}

```

At this moment, the laptop has 16.04 installed on it.  I had the same exact issues with 14.04  Any help at this point would be greatly appreciated.  I've been struggling with this for hours now.

---

### Post by Gillingham on 2016-08-31
When you say you reinstalled lightDM -  did you purge the package before installing it or "just" reinstalled it. 

I ask because on my upgrade from 14.04 to 16.04 I had a similar issue and  I had to do this procedure before I succeeded.  

```
sudo apt-get purge nvidia*
sudo apt-get purge lightdm 
sudo apt-get install lightdm 
sudo apt-get install mesa-utils
sudo apt-get install ubuntu-desktop

```

I had to install mesa-utils because of my graphics card, so you may need to reinstall the nvidia drivers afterwards (or try the nouveau drivers).  Purging lightdm or nvidia removed ubuntu-desktop so I thought it best to install that as well.

My apologies I can't find a reference for why I did this.

David

---

### Post by CrunchaliciousCaptain on 2016-09-07
Sorry for the delayed response.  I've been busy with other things and haven't had the opportunity to try your solution.  I just gave it a shot and it didn't work.  I had previously used purge to uninstall before reinstalling, anyway.  Here's .xsession-errors in full:

```

Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: gnome-session (Unity) main process (2299) terminated with status 1
init: unity-settings-daemon main process (2280) killed by TERM signal
init: logrotate main process (2173) killed by TERM signal
init: update-notifier-crash (/var/crash/lightdm.0.crash) main process (2210) killed by TERM signal
init: update-notifier-rash (/var/crash/_usr/_sbin_aa-status.1000.crash) main process (2213) killed by TERM signal
init: xsession-init main process (2272) killed by TERM signal
init: unity-panel-service main process (2308) killed by TERM signal
init: Disconnected from notified D-Bus bus

```

---

