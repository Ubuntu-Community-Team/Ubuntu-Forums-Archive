---
title: "apt-get or Aptitude?"
date: 2015-02-13
forum: General Help
---

### Post by garycheng12 on 2015-02-13
For beginners, apt-get or aptitude is a of preference and basic tools are available to both. I want to know the differences between the two in terms of usability, availability of tools, effective of tools, general popularity and trend, etc. so I can choose one that fits me better. I expect to thoroughly use the tools available to understand package management.

---

### Post by kerry_s on 2015-02-13
they both get the job done. it's personal preference but you should learn to use both.
apt-get is my choice, it is by far the most popular. aptitude is not even installed by default in most, so you have to apt-get it anyways.

i use a .bash_aliases file to shorten typing, so i don't even think about it.

---

### Post by bapoumba on 2015-02-13
A little bit of reading : [https://www.debian.org/doc/manuals/debian-faq/ch-pkgtools.en.html](https://www.debian.org/doc/manuals/debian-faq/ch-pkgtools.en.html)

I used to use aptitude a lot in the previous days where some functionalities were not implemented in apt-get (the autoremove for ex), for its integration and better dependency problems solver. But now I just use apt-get.

---

### Post by dragonfly41 on 2015-02-13
Another good read ..

[http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)

---

### Post by bapoumba on 2015-02-13
> **dragonfly41 said:**
> Another good read ..

[http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)

Thanks !
I love nano though :)

---

### Post by maclenin on 2015-02-13
My [few cents worth]("http://ubuntuforums.org/showthread.php?t=2240291")!

I tend to prefer **aptitude** - more broadly - and use it almost exclusively for updating my system / installing new software....
```
sudo aptitude update
sudo aptitude safe-upgrade
```
However, **apt-get** has the autoremove command (which aptitude does not have and) which is useful for removing old kernels....
```
sudo apt-get autoremove
```

I have also inferred from additional reading - [see within my link, above]("http://ubuntuforums.org/showthread.php?t=2240291&p=13105743#post13105743") - that **aptitude** tends to be more comprehensive in addressing / resolving dependency issues.

No show-stoppers, either way.

---

### Post by ian-weisser on 2015-02-13
> **garycheng12 said:**
> I want to know the differences between the two in terms of usability, availability of tools, effective of tools, general popularity and trend, etc. so I can choose one that fits me better. I expect to thoroughly use the tools available to understand package management

Simply try each one for a few weeks.
They both work well.
Then decide...recognizing that circumstances may change your decision, and knowing *both* is best.

---

### Post by efflandt on 2015-02-13
If I know what I want to install or purge, apt-get works fine.

If I do not know what to install or purge and X is running, I use synaptic (no longer installed by default) which is easy to search for packages. Software Center seems to lack details, especially for non-default versions of packages with multiple versios (video drivers, removing old kernels, etc.).

If X is not working for some reason and I do not know what to install (or purge) I use aptitude, which is awkward (for me) compared to synaptic, but relatively easy to search for packages.

---

