---
title: "can't install compiz fusion"
date: 2007-06-24
forum: General Help
---

### Post by tronica on 2007-06-24
i found a guide on here to install compizfusion, and i get errors when trying to install it.

```
tronica@desktop:~$ sudo apt-get install compiz-fusion-*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting compiz-fusion-plugins-extra for regex 'compiz-fusion-*'
Note, selecting compiz-fusion-plugins-unsupported for regex 'compiz-fusion-*'
Note, selecting compiz-fusion-plugins-main for regex 'compiz-fusion-*'
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  compiz: Depends: compiz-decorator
  compiz-gnome: Depends: compiz-gtk (= 1:0.3.6-1ubuntu13) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
tronica@desktop:~$ 
```

when i do the apt-get -f install

```
tronica@desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  compiz-gnome
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B/165kB of archives.
After unpacking 1294kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 115510 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.1+git20070622~3v1ubuntu4_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070622~3v1ubuntu4_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070622~3v1ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
tronica@desktop:~$ 
```

i can't figure out what the deal is. any ideas?

---

### Post by Happy_Man on 2007-06-24
I opened up Synaptic and forced compiz-gnome to install when I got your problem. As of right now, I don't have compiz-gtk installed, but Compiz Fusion does fine. Try that....

---

### Post by tronica on 2007-06-24
that worked thanks.

---

