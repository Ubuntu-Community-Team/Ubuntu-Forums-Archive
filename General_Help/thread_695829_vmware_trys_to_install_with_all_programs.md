---
title: "vmware trys to install with all programs"
date: 2008-02-13
forum: General Help
---

### Post by LEDZO on 2008-02-13
I've been trying to install nmap but when ever i try to install anything it always ends up giving me a ELUA for vmware that i can't get out of. I finally noticed that when ever i try to install anything, even dpkg, it also tries to install vmware again. After i get the ELUA, if i try to install something it gives me

```
dpkg interupted, fix it by running dpkg --configure -a
```

so i do and it gives me a blank prompt so i assume it worked, but it goes in that cycle every time

```


profoak@000:~$ sudo apt-get install nmap
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  vmware-server
The following NEW packages will be installed:
  nmap
The following packages will be upgraded:
  vmware-server
1 upgraded, 1 newly installed, 0 to remove and 183 not upgraded.
1 not fully installed or removed.
Need to get 0B/80.2MB of archives.
After unpacking 133MB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

as you can see it keeps trying to install vmware as an extra package

---

