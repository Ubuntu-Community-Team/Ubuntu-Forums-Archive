---
title: "Remove pulse from 12.04"
date: 2012-11-14
forum: General Help
---

### Post by blm14 on 2012-11-14
So I just moved from 10.04 to 12.04 and am liking it so far. I want to remove pulse (for various reasons) and just use ALSA. 

On prior distros this would usually work:

```

$sudo apt-get autoremove pulseaudio

```

But this time around I am seeing some disturbing packages that would get removed:

```


Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  indicator-sound libcanberra-pulse libgle3 libjpeg-progs libjpeg-turbo-progs
  liblaunchpad-integration1 pulseaudio pulseaudio-module-bluetooth
  pulseaudio-module-gconf pulseaudio-module-x11 ubuntu-desktop
  xscreensaver-data xscreensaver-gl
0 upgraded, 0 newly installed, 13 to remove and 0 not upgraded.
After this operation, 6,367 kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```

Why should it be necessary to remove the package "ubuntu-desktop?" That sounds rather important!

Can that package be removed safely without screwing anything up? Is just autoremove pulseaudio going to remove pulse and bring back to vanilla alsa or will it completely munge my sound? I'm sure the answers to these questions are simple but I want to be safe...

---

### Post by blm14 on 2012-11-15
bump

---

### Post by Dennis N on 2012-11-15
'ubuntu-desktop' is a **metapackage**:

[http://askubuntu.com/questions/66257/what-is-the-difference-between-a-meta-package-and-a-package](http://askubuntu.com/questions/66257/what-is-the-difference-between-a-meta-package-and-a-package)

Read the first answer for the above question posted at Ask Ubuntu for an explanation which answers your question.

If the removal will result in other problems, I can't say.

---

