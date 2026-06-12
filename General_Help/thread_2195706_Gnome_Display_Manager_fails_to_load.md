---
title: "Gnome Display Manager fails to load"
date: 2013-12-25
forum: General Help
---

### Post by ggodone on 2013-12-25
I just installed Ubuntu GNOME, and I decided to install the font render-er [Infinality]("http://www.webupd8.org/2013/06/better-font-rendering-in-linux-with.html")   as the default font rendering was bugging me. So I restarted my  computer, selected the linux partition, and was met with a black screen  after the GNOME loading screen. I tried safe mode and it said that Gnome  Display Manager failed (when booting up it said Starting Gnome Display Manager ... [Fail]).


In root shell prompt I tried entering  ```
sudo apt-get purge fontconfig-infinality
sudo apt-get install ppa-purge
sudo ppa-purge ppa:nolwantdthisname/ppa
```
  But with every command I got

  ```
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt
E: The package lists or status file could not be parsed or opened
```
 
 
What can I do?

---

