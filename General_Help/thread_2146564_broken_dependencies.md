---
title: "broken dependencies"
date: 2013-05-18
forum: General Help
---

### Post by frazerr on 2013-05-18
Hi,

sorry i have no idea how to fix this

when I try to install things  I get

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 e17 : Depends: libefl-bin (>= 201200000000) but it is not going to be installed
 x : Depends: x (>= 1:x) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



and when I try

 sudo apt-get install -f


-->
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libfm-data orage libmenu-cache1 psensor-common libfm-gtk1 lxmenu-data libfm1 xfce4-appfinder lxshortcut gtk2-engines-xfce xfce4-mixer
  libfm-gtk-data
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libefl-bin
The following NEW packages will be installed:
  libefl-bin
0 upgraded, 1 newly installed, 0 to remove and 155 not upgraded.
1 not fully installed or removed.
Need to get 0 B/315 kB of archives.
After this operation, 914 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 284545 files and directories currently installed.)
Unpacking libefl-bin (from .../libefl-bin_201305180806-22172~precise1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libefl-bin_201305180806-22172~precise1_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/embryo_cc', which is also in package libembryo0 201208301153-474~precise1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libefl-bin_201305180806-22172~precise1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)




any help please

---

### Post by Zestypanda on 2013-05-18
It's because the ppa has been removed or is no longer available.

---

### Post by frazerr on 2013-05-20
how do I fix it?

its affecting anything I try to install.

---

### Post by Frogs Hair on 2013-05-20
Start with the link if using a PPA.  [http://www.webupd8.org/2012/11/install-ppa-purge-with-multi-arch.html](http://www.webupd8.org/2012/11/install-ppa-purge-with-multi-arch.html)

If these are E17 packages from the Ubuntu repository they should have worked because I installed them on 12.04.

---

### Post by frazerr on 2013-05-20
I dont know what any of that is.

My computer is working fine except I cant install anything new.

Can someone give me a command that will fix up the dependency tree.

---

### Post by gifford on 2013-05-20
Use Synaptic Package manager to fix the broken packages. Go to edit in synaptic, then fix broken packages.
Here is a link for doing it with the command line: [http://askubuntu.com/questions/30993/fixing-broken-packages](http://askubuntu.com/questions/30993/fixing-broken-packages)

---

### Post by Frogs Hair on 2013-05-20
> **frazerr said:**
> I dont know what any of that is.

My computer is working fine except I cant install anything new.

Can someone give me a command that will fix up the dependency tree.


How did you attempt to install E17 ?



> e17 : Depends: libefl-bin (>= 201200000000) but it is not going to be installed
 x : Depends: x (>= 1:mad:) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


---

### Post by frazerr on 2013-05-20
Thanks,

editing dpkg status   worked.  thank you


I was given this computer and had never heard of e17.

thanks for your help every one

much appreciated

---

### Post by Frogs Hair on 2013-05-21
E17 is a desktop environment and now that it is installed it can be selected from the icon on the login screen and used. If you don't want it causing future problems or you don't like it use the following. ```
sudo apt-get remove e17
```

---

