---
title: "&quot;cleaning&quot; Ubuntu?"
date: 2007-02-09
forum: General Help
---

### Post by zeroblitzt on 2007-02-09
Two questions, but the title describes my main one:

1) Is there a way to "clean" old files from Ubuntu? My main issue is the kernels. Like, I don't need 4 kernels on my boot screen, only 1 (I guess this is just in case  you reboot and one kernel doesn't work or something). Or are old kernel images deleted after a certain number of new ones have been downloaded? 

2) In the System Monitor, it shows /dev/hdc1 (where Ubuntu is installed) as having 32.7 gigs of space free, yet only 30.7 are available. What is Ubuntu doing with my missing 2.0 gigs?

---

### Post by llamakc on 2007-02-09
1. Remove the old kernels with Synaptic/aptitude/apt-get and the entries will be removed from menu.lst

2. I don't use Gnome's System Monitor, so I don't know. You can check in the Terminal with:

`df -h`

Swap space maybe?

---

