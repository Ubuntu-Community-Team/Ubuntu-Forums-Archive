---
title: "Trouble installing Java VM"
date: 2007-08-20
forum: General Help
---

### Post by Gideon Stargrave on 2007-08-20
```
bacon@sporkwieldingferret:~$ sudo apt-get install -f sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  firefox
Suggested packages:
  firefox-gnome-support latex-xft-fonts firefox-libthai
The following NEW packages will be installed:
  firefox sun-java6-fonts sun-java6-plugin
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 9266kB of archives.
After unpacking 29.5MB of additional disk space will be used.

```

It wants to install Firefox, but I already have firefox. It doesn't show up in Apt because I had to install a non-repository version.

Is there a way to either force it to install, or make it able to read my existing firefox as a workable install? Or any other way to install the thing? I just want the java browser plugin. x.x

---

