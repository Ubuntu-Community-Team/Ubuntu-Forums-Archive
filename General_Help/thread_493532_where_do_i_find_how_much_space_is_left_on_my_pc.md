---
title: "where do i find how much space is left on my pc"
date: 2007-07-05
forum: General Help
---

### Post by zig1234 on 2007-07-05
im of course running ubuntu

---

### Post by llamakc on 2007-07-05
In a Terminal or console you can type the command

```

df -h


```

The "-h" option outputs the results in a human-readable format so it ends up looking like this (for my system):

```

ken@llamakc 08:40:28:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              49G   12G   35G  26% /
varrun                506M  1.1M  505M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  100K  506M   1% /proc/bus/usb
udev                  506M  100K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-16-generic/volatile
/dev/sda3              98G   26G   68G  28% /home
/dev/hdc1              25G  460M   23G   2% /media/hdc1
/dev/hdc2              50G  9.4G   38G  20% /media/hdc2

```

Instead of like this (without the "-h" flag)

```

ken@llamakc 08:40:31:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             50403028  12147472  35695200  26% /
varrun                  517888      1076    516812   1% /var/run
varlock                 517888         0    517888   0% /var/lock
procbususb              517888       100    517788   1% /proc/bus/usb
udev                    517888       100    517788   1% /dev
devshm                  517888         0    517888   0% /dev/shm
lrm                     517888     33788    484100   7% /lib/modules/2.6.20-16-generic/volatile
/dev/sda3            102428092  26526152  70698892  28% /home
/dev/hdc1             25196436    470136  23702320   2% /media/hdc1
/dev/hdc2             51723896   9764640  39331828  20% /media/hdc2

```

HTH

---

### Post by dagrump on 2007-07-05
Places>home, look in lower left corner. Should show free space for /home. It would depend on your partitioning as to whether that accurate.

---

### Post by szf on 2007-07-05
Download Baobab from the repositories and it will tell you all you need.

---

### Post by llamakc on 2007-07-05
> **szf said:**
> Download Baobab from the repositories and it will tell you all you need.

Baobab is provided by the package "gnome-utils" and is installed by default in Ubuntu.

OP, if you want to use a graphical tool to view the state of free space on your hard disks, do this:

type ALT+F2 to get the run application dialog.

In that, type "baobab".

---

### Post by Brucevdk on 2007-07-05
Another method would be the *gnome-system-monitor*'s *File Systems* tab.

---

### Post by szf on 2007-07-07
> **llamakc said:**
> Baobab is provided by the package "gnome-utils" and is installed by default in Ubuntu.
That's true as of Ubuntu 7.04 (Feisty). One forgets after a while what they installed and what would be in a fresh Ubuntu image.

---

### Post by llamakc on 2007-07-07
> **szf said:**
> That's true as of Ubuntu 7.04 (Feisty). One forgets after a while what they installed and what would be in a fresh Ubuntu image.

That's a wonderful point to make. I didn't take that into consideration. It should also be noted that any particular program or file can be searched for over at [http://packages.ubuntu.com](http://packages.ubuntu.com). I see that baobab was its own package in Breezy and Dapper, and then moved to gnome-utils after Edgy.

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=baobab&searchon=all&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=baobab&searchon=all&subword=1&version=all&release=all)

---

