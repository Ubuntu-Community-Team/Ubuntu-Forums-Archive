---
title: "Aptitude wants CD-ROM while connected to net"
date: 2007-01-31
forum: General Help
---

### Post by MrLeviticus on 2007-01-31
The package manager asks me for my install CD-ROM when I try and apt-get any packages. I have a fully functional internet connection and a fresh install of Xubuntu. Any ideas?

Thanks in advance!

(Keep up the great work)

---

### Post by taurus on 2007-01-31
Open a terminal and edit /etc/apt/sources.list

```
sudo nano -w /etc/apt/sources.list
```
and place a # in front of the line that has CD-ROM in it (usually first line or near the top) to comment it out.  Save it by holding down <Ctrl> while pressing x.  Then answer the question with Y and Return.

Now, run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by chalex on 2007-01-31
Or if you're using Synaptic, go to the Repositories dialog and disable the CD ones.  It will then comment that line for you. :)

---

