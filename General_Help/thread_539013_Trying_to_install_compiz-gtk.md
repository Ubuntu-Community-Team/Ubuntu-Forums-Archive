---
title: "Trying to install compiz-gtk"
date: 2007-08-30
forum: General Help
---

### Post by s_h_a_d_o_w_s on 2007-08-30
```
giga@UbuntuZilla:~$ sudo apt-get install compiz-gtk
Password:
Reading package lists... Done
Building dependency tree        
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  compiz: Depends: compiz-decorator
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
giga@UbuntuZilla:~$ 
```

So:

```
giga@UbuntuZilla:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  compiz-gnome
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
1 not fully installed or removed.
Need to get 0B/167kB of archives.
After unpacking, 909kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 112107 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.5~git20070827+jbs0_amd64.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20070827+jbs0_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20070827+jbs0_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
giga@UbuntuZilla:~$ 


```

I need it for compiz-fusion, feisty amd64 :)

---

### Post by Happy_Man on 2007-08-30
Yeah.... I had the same problem when I was first installing Compiz Fusion, back in the days when there was only one thread about it on the entire forum. :o

Remove (including all config files) the entire compiz package group, and install again. Don't install compiz-gtk, though. Open up synaptic and manually force compiz-gnome. That's what worked for me.... perhaps it will work for you, too.

---

