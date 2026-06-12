---
title: "from ubuntu 12.04 to Xubuntu 12.04"
date: 2012-10-21
forum: General Help
---

### Post by aspergerian on 2012-10-21
My Acer-1410 was running well with Ubuntu 9.04 with all data files in separate partition. Installation of Ubuntu 12.04 generated two major partitions on the 250g HD. 9.04 remains in one partition. 12.04 is installed separately in its own partition. I prefer classic desktop. Ubuntu 12.04 has many features I don't want and seems to run slowly on my Acer. 

I would like to install Xubuntu 12.04 on the partition now being occupied by Ubuntu 12.04 but don't want to overwrite data in 9.04 partition. Alternatively, I would be happy to install Xubuntu 12.04 on entire HD if data in 9.04 partition could be retained.

Guidance would be appreciated. A screenshot of gparted taken from U-12.04 partition is included.

---

### Post by 2F4U on 2012-10-21
You could either install xubuntu-desktop from your running Ubuntu 12.04. This would allow you to select which desktop environment to start at the login screen. However, Ubuntu 12.04 is still installed.
If you intend to replace Ubuntu 12.04 with Xubuntu 12.04 you can select "Something else" in the partitioning screen of the Xubuntu 12.04 installer and select your Ubuntu 12.04 partitions as target for the installation. This will completely override Ubuntu 12.04 with Xubuntu 12.04.
If you data in 9.04 is on a seperate partition, you could also install Xubuntu 12.04 over both Ubuntu versions, but keep the data partiton from 9.04 untouched.

---

### Post by cmcanulty on 2012-10-21
just install Xubuntu-desktop and pick it at login won't remove anything

---

### Post by dino99 on 2012-10-21
there is no much difference between ubuntu & xubuntu: the diff is only the desktop used. By the way with ubu PP if you does not like gnome-shell and/or unity, then you can still use gnome-classic:
- via synaptic, purge ubuntu-desktop, unity & GS & their dependencies
- install gnome-session-fallback (and you get what you like)
- instead if you really move to xubuntu, then install the xubuntu-desktop, then clean the system (autoremove/deborphan)

but Lubuntu can also run better on your hardware. :P

---

### Post by aspergerian on 2012-10-21
I did a fresh install of Xubuntu 12.04.1 (64 bit), having first backed up my 9.04's /home to an external HD. Now I'll have to learn how to get my external-backup of /home properly into my new install of Xu 12.04.1.

Thank you to those who replied.

---

### Post by cmcanulty on 2012-10-21
I believe you can just copy all the files in your /home backup into the new /Home

---

