---
title: "Come back repositories!!!"
date: 2007-02-17
forum: General Help
---

### Post by Entity` on 2007-02-17
twice now Ive tried to upgrade via the internet, once I cancelled because of the sheer size of the upgrade and the second time I failed because my connection was lost.  Now after the second time I get this for my universe and multiverse reposetories:

     W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)

and:

     [http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

and:

     W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)

What can I do to get the repositories back???!?:confused:

---

### Post by taurus on 2007-02-17
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the **us.** from your repos.  Save it and then run

```
sudo aptitude update
sudo aptitude upgrade
```

---

