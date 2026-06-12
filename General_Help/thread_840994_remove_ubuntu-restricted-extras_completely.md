---
title: "remove ubuntu-restricted-extras completely"
date: 2008-06-25
forum: General Help
---

### Post by bagm on 2008-06-25
Hi,
I installed ubuntu-restricted-extras package which downloaded and installed like 100+ MB of packages.
Now I want to remove those packages from my system, but if I 

sudo apt-get remove ubuntu-restricted-extras

only that package is removed, not the packages that were installed by it.

How can I remove them?

TIA.

---

### Post by cdtech on 2008-06-25
sudo apt-get remove --purge ubuntu-restricted-extras

Should remove the extras.

---

### Post by bagm on 2008-06-25
john@john-desktop:~$ sudo apt-get remove --purge ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ubuntu-restricted-extras*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 32.8kB disk space will be freed.
Do you want to continue [Y/n]?

---

### Post by shae on 2008-06-26
Remove ubuntu-restricted-extras.  Then in synaptic under status, you will see a list of packages that are autoremovable.  The packages installed by ure that you are not making use of should be listed in there.

---

### Post by Vivaldi Gloria on 2008-06-26
ubuntu-restricted-extras is just a dummy package. It actually installs the following:

various gsteamer plugins
flashplugin-nonfree
icedtea-gcjwebplugin
libdvdread3
liblame0
msttcorefonts
unrar

Uninstall the ones you want.

---

### Post by bagm on 2008-06-26
> **shae said:**
> Remove ubuntu-restricted-extras.  Then in synaptic under status, you will see a list of packages that are autoremovable.  The packages installed by ure that you are not making use of should be listed in there.

I can't find them. How's exactly called that list in synaptic?

---

### Post by jimdawg_80 on 2009-05-05
jimmie@nobody:~$ sudo apt-get remove --purge ubuntu-restricted-extras
[sudo] password for jimmie: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
jimmie@nobody:~$ 
what do i do from here?

---

### Post by wfp on 2009-05-05
You should have started your own thread. Open a terminal and run>
sudo dpkg --configure -a

---

### Post by konqueror7 on 2009-05-05
then just do a,
```
sudo apt-get autoremove --purge ubuntu-restricted-extras
```

...now this will remove unnecessary packages and its configs, now do as *Vivaldi Gloria* said...

---

