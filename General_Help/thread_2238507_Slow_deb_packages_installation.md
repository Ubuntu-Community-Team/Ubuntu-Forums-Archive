---
title: "Slow deb packages installation"
date: 2014-08-08
forum: General Help
---

### Post by startas on 2014-08-08
Is there a way to speed up ubuntu deb packages installation(system updates, ppa's, other deb packages) ? Its no secret, that deb packages installation is really slow, its like 5-10 times slower than using pacman in arch linux and arch based distros, its a shame how slow it is in ubuntu... Is there anything i can do to improve it ? Any hacks, disabling keys check, disabling checksum, anything ?

---

### Post by ian-weisser on 2014-08-08
Hmmm. My apt sessions seem very fast. So it was a secret to me.

Does your lack of speed occur during the dkpg database update (choose a faster mirror), the download (choose a faster mirror), or the actual installation (cannot change)?

---

### Post by tgalati4 on 2014-08-08
I would be interested in some data.  Install a particular package (say *gimp*) and time it in both pacman and apt.  Then remove the package (with purge) in both and then reinstall and see if there is a speed difference.  There are some tips to improve the dpkg cache speed--you will have to search for them on these forums.

---

### Post by ajgreeny on 2014-08-08
What exactly do you mean by "slow"?
  In comparison with any other distros I have ever used, admittedly for only a short time, but including PCLinuxOS, OpenSuse, Fedora, CentOS, I find Ubuntu and its deb installation much faster, so I wonder if there is some configuration that you have which for some reason is not set up as it should be.

A minor help it may be but if you do not use applications in different languages than (in my case) English, and I presume this also works for other languages but can not be certain of that, you can speed up the refreshing of repos by not downloading all the language related updates.  Those are the lines in **sudo apt-get update** output that always start with **Ign** and mention **translation** in the line somewhere.

Add the line
```
Acquire::Languages "none";
```
to the /etc/apt/apt.conf.d/00aptitude file.

Many thanks to p34 of this month's Linux Format magazine here in UK.  I have tried it and it works.

---

### Post by startas on 2014-08-08
Its not the files download time, its the package installation time. In arch linux, installing, lets say, firefox, is like 1-2 seconds, whereas in ubuntu installing firefox would take at least 10 seconds. I tried installing gimp, in arch it takes 4 seconds (only install time, without download time), and i installed gimp some time ago on ubuntu, it took a long time.

---

