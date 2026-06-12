---
title: "problem installing gtkpod"
date: 2007-10-24
forum: General Help
---

### Post by gnychis on 2007-10-24
Hi all,

Having trouble installing GTKPod:

```

gnychis@monster:~$ sudo apt-get install gtkpod
[sudo] password for gnychis:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gtkpod is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gtkpod: Depends: libgpod2 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

gnychis@monster:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libgpod2
The following NEW packages will be installed:
  libgpod2
0 upgraded, 1 newly installed, 0 to remove and 10 not upgraded.
1 not fully installed or removed.
Need to get 0B/181kB of archives.
After unpacking 385kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 140069 files and directories currently installed.)
Unpacking libgpod2 (from .../libgpod2_0.5.2-2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libgpod2_0.5.2-2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libgpod.so.2.0.0', which is also in package libgpod1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libgpod2_0.5.2-2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

- George

---

### Post by gnychis on 2007-11-13
bump, i can't upgrade or install any other packages until this is fixed, i would greatly appreciate the help

---

### Post by gnychis on 2007-11-14
^

---

### Post by ThrobbingBrain66 on 2007-11-14
I would try to remove libgpod1 first, as I believe libgpod2 is its replacement.
```
sudo apt-get remove --purge libgpod1
```

---

### Post by timcredible on 2007-11-14
why are you installing gtkpod?  rhythmbox and amarok are better and they both support ipods.

---

### Post by gnychis on 2007-11-15
> **ThrobbingBrain66 said:**
> I would try to remove libgpod1 first, as I believe libgpod2 is its replacement.
```
sudo apt-get remove --purge libgpod1
```

```

gnychis@monster:~$ sudo apt-get remove --purge libgpod1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gtkpod: Depends: libgpod2 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

