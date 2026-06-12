---
title: "/var/ is full"
date: 2018-05-09
forum: General Help
---

### Post by razialexis43 on 2018-05-09
Hello everyone, I keep getting the error that /var/ is full and that I should clean it up. I have no problem with log files. Basically what happens is that /var/lib/snapd is 5.2 GB. I have a total of 10GB allocated for /var/. Is it safe to delete that folder?
I am not very experienced with Linux in general, so any advice is welcome. Thank you!

---

### Post by Holger_Gehrke on 2018-05-09
The directory /var/lib/snapd/snaps is where all applications that where installed as snap packages go. There is also a cache directory in /var/lib/snapd/cache. And of course there's also the cache directory for packages installed or updated through apt in /var/cache/apt/packages. The first of these you probably don't want to remove - you installed those programs, and the snap-files are needed for them to work; the second one I don't know whether or not it's safe to simply remove the files in there. Cleaning up the apt-cache is well documented (and not what you asked for), but for completeness sake: 'sudo apt-get clean' removes all cached .deb-packages from that directory.

Holger

---

### Post by ajgreeny on 2018-05-09
Might this be the same problem as the one  discussed at [https://ubuntuforums.org/showthread.php?t=2388837](https://ubuntuforums.org/showthread.php?t=2388837) ?

---

