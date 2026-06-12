---
title: "Stuck with dpkg returned an error code"
date: 2017-02-16
forum: General Help
---

### Post by bizhat on 2017-02-16
When i try to remove kbuntu-desktop, i get following error


```

root@git:~# apt remove -f kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kde-telepathy-minimal : Depends: kde-config-telepathy-accounts (>= 15.04.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@git:~# 

```

When i run apt-get -f install, i get

```

root@git:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  kde-config-telepathy-accounts
The following NEW packages will be installed:
  kde-config-telepathy-accounts
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
676 not fully installed or removed.
Need to get 137 kB of archives.
After this operation, 825 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 kde-config-telepathy-accounts amd64 4:15.12.3-0ubuntu1 [137 kB]
Fetched 137 kB in 0s (887 kB/s)                       
(Reading database ... 302656 files and directories currently installed.)
Preparing to unpack .../kde-config-telepathy-accounts_4%3a15.12.3-0ubuntu1_amd64.deb ...
Unpacking kde-config-telepathy-accounts (4:15.12.3-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.12.3-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/accounts/services/google-im.service', which is also in package account-plugin-google 0.12+16.04.20160126-0ubuntu1
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Errors were encountered while processing:
 /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.12.3-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@git:~# 

```

I tried apt-get clean, still same problem.

```

root@git:~# apt-get clean
root@git:~# apt-get install openvpn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openvpn is already the newest version (2.3.10-1ubuntu2).
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kde-telepathy-minimal : Depends: kde-config-telepathy-accounts (>= 15.04.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@git:~# 

```

I am on Ubuntu 16.04

```

root@git:~# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:   xenial
root@git:~# 

```

Any idea how i fix this ?

---

### Post by bizhat on 2017-02-16
I got it fixed by 

```

root@git:~# dpkg -r --pending
dpkg: dependency problems prevent removal of kde-telepathy-minimal:
 kde-telepathy depends on kde-telepathy-minimal (= 15.04.20ubuntu1); however:
  Package kde-telepathy-minimal is to be removed.

dpkg: error processing package kde-telepathy-minimal (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 kde-telepathy-minimal
root@git:~# dpkg --purge kde-telepathy
(Reading database ... 302654 files and directories currently installed.)
Removing kde-telepathy (15.04.20ubuntu1) ...
root@git:~# dpkg -r --pending
(Reading database ... 302651 files and directories currently installed.)
Removing kde-telepathy-minimal (15.04.20ubuntu1) ...
root@git:~# 

```

---

