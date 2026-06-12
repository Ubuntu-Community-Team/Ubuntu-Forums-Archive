---
title: "Complete firefox uninstall - unable to revert firefox tweaks, need to fresh install"
date: 2012-11-17
forum: General Help
---

### Post by Justin C on 2012-11-17
**Distro:**
[http://www.linuxmint.com/download_lmde.php](http://www.linuxmint.com/download_lmde.php)


**Problem:**
The out of the box version of firefox provided from the distro above did exactly what I needed and worked well. After some tweaking in regards to addons, problems have started to occur when visiting some websites that previously had no problems.


**Need help:**
Completely removing every file that has to do with firefox on this machine, so I can do a fresh install. 

I have tried to accomplish this in ways that I will list below, however each time I have done them, when I re-install firefox the problems still remain. This is because I'm not doing a proper complete removal I'm guessing, evidence supporting this also exists because on first startup of the newly installed firefox it will display "checking the compatibility of your currently installed icons" with a list of all the addons I supposedly would have deleted :confused: :confused:


**Tried:**
sudo apt-get remove firefox
&
sudo apt-get --purge remove firefox
&
launching synaptic package manager and marking all firefox files for complete removal, then removing them.



_Thanks!_

---

### Post by VooDooSyxx on 2012-11-17
Pop open a terminal and move your old firefox directory out of the way. Doing a purge will remove all firefox system files, but it won't touch any of your local settings so after reinstall it's still seeing your locally installed extensions and tweaks. 

```

$ mv .mozilla  .mozilla.bak

```

---

### Post by Justin C on 2012-11-17
> **VooDooSyxx said:**
> Pop open a terminal and move your old firefox directory out of the way. Doing a purge will remove all firefox system files, but it won't touch any of your local settings so after reinstall it's still seeing your locally installed extensions and tweaks. 

```

$ mv .mozilla  .mozilla.bak

```

Yeah buddy!

Knew it was this simple just didn't know where to look.

Thank-you.

---

