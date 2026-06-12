---
title: "Missing network manager icon on Ubuntu 14.04 amd64"
date: 2014-05-05
forum: General Help
---

### Post by giordan on 2014-05-05
Hi all,
I made a clean installation of Ubuntu 14.04 on my PC.
I had several problem at the beginning, since after a "sudo apt-get -f install" to install dependencies of packages many already installed packages were removed (I don't know why, even "ubuntu-desktop" was removed :-? ). However, now it seems that I have recovered all.
But since from my first boot I don't have the network manager icon in the bar near the clock.

I have seen that this is a known bug in Lubuntu, but I have not found anything related to Ubuntu.
I have found that a possible solution can be:

```
[B]
sudo service network-manager stop[/B][B]
sudo rm /var/lib/NetworkManager/NetworkManager.state[/B] 
**sudo service network-manager start**

```

but it doesn't work for me, even because network-manager service seems not to be running (by clicking TAB after **sudo service netw** it is completed with **sudo service networking**).
However, in the system monitor the nm-applet application is running.

Anyone else has experienced this problem and has a solution?

Thanks.

---

### Post by giordan on 2014-05-12
Today the network manager icon appeared for the first time, after having installed some updates and having rebooted.
Maybe it was a bug which appeared only on some architectures that now has been solved (at least for mine).

Regards.
MG

---

### Post by Slaan on 2015-04-28
Work for me with 14.02.2 :

sudo apt-get install indicator-applet-complete

---

