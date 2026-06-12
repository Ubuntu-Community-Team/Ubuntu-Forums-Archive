---
title: "Error during 16.04 to 18.04 (LTS) upgrade"
date: 2019-05-30
forum: General Help
---

### Post by boomshakalaka1 on 2019-05-30
I just tried to upgrade my server from 16.04 to 18.04 via do-release-upgrade.  It finished like so:

```

Errors were encountered while processing:
python3-apt
update-notifier-common
isc-dhcp-client
python3-distupgrade
update-manager-core
ubuntu-release-upgrader-core

Upgrade complete

The upgrade has completed but there were errors during the upgrade process.

```

I'm afraid to reboot as things seem pretty broken right now.  Trying to do anything with apt results in some unmet dependency errors which seem pretty fundamental:

```

$ sudo apt-get upgrade     
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 isc-dhcp-client : Depends: libdns-export1100 but it is not installed
                   Depends: libisc-export169 but it is not installed
 python3-apt : Depends: libapt-inst2.0 (>= 1.6.5~) but 1.2.31 is installed
               Depends: libapt-pkg5.0 (>= 1.6.5~) but 1.2.31 is installed
 systemd : Depends: libsystemd0 (= 229-4ubuntu21.21) but 237-3ubuntu10.21 is installed
E: Unmet dependencies. Try using -f.

```

I'd greatly appreciate any suggestions on how to resolve this.

---

### Post by boomshakalaka1 on 2019-05-30
The closest thing I've been able to find to this problem was this question on Ask Ubuntu:
[https://askubuntu.com/questions/1094404/upgrading-from-16-04-to-18-04-error-unmet-dependencies](https://askubuntu.com/questions/1094404/upgrading-from-16-04-to-18-04-error-unmet-dependencies)

Unfortunately there was no solution posted.  Hopefully there is a way to fix this??

---

### Post by cruzer001 on 2019-05-30
So what happens when you use the -f switch?

---

### Post by boomshakalaka1 on 2019-05-30
I haven't tried that yet, I was afraid that might break things further?

---

### Post by cruzer001 on 2019-05-30
No, its a repair command that may save the day :)
Please post the output.

---

### Post by boomshakalaka1 on 2019-05-30
```

$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  cgmanager fonts-ubuntu-font-family-console libcryptsetup4 libdns-export162 libisc-export160
  python3.5 python3.5-minimal rename
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  apt apt-transport-https apt-utils libapt-inst2.0 libapt-pkg5.0 libdns-export1100
  libgnutls-openssl27 libgnutls30 libidn2-0 libisc-export169 libpam-systemd libtasn1-6 libunistring2
  networkd-dispatcher systemd
Suggested packages:
  apt-doc aptitude | synaptic | wajig dpkg-dev gnutls-bin systemd-container
The following packages will be REMOVED:
  systemd-shim
The following NEW packages will be installed:
  libdns-export1100 libidn2-0 libisc-export169 libunistring2 networkd-dispatcher
The following packages will be upgraded:
  apt apt-transport-https apt-utils libapt-inst2.0 libapt-pkg5.0 libgnutls-openssl27 libgnutls30
  libpam-systemd libtasn1-6 systemd
10 upgraded, 5 newly installed, 1 to remove and 401 not upgraded.
8 not fully installed or removed.
Need to get 0 B/7,289 kB of archives.
After this operation, 1,193 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 65314 files and directories currently installed.)
Removing systemd-shim (9-1bzr4ubuntu1) ...
Removing 'diversion of /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service to /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service.systemd by systemd-shim'
dpkg-divert: error: rename involves overwriting '/usr/share/dbus-1/system-services/org.freedesktop.systemd1.service' with
  different file '/usr/share/dbus-1/system-services/org.freedesktop.systemd1.service.systemd', not allowed
dpkg: error processing package systemd-shim (--remove):
 installed systemd-shim package post-removal script subprocess returned error exit status 2
Errors were encountered while processing:
 systemd-shim
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by boomshakalaka1 on 2019-05-30
OK, I just renamed the file per the answer given here:
[https://askubuntu.com/questions/838491/dpkg-divert-error-rename-involves-overwriting-error-after-upgrading-from-16-04](https://askubuntu.com/questions/838491/dpkg-divert-error-rename-involves-overwriting-error-after-upgrading-from-16-04)

And now apt-get seems functional again...  Continuing with apt-get upgrade, fingers crossed...

---

### Post by cruzer001 on 2019-05-30
Hummm

What going on with systemd-shim?
```
apt-cache policy systemd-shim
```

And 401 pkgs not upgraded, lets have a look at your sources.
```
cat /etc/apt/souces.list && ls /etc/apt/sources.list.d/*.list
```

---

### Post by cruzer001 on 2019-05-30
Ok, just seen your other post.  Fingers crossed :)

---

### Post by boomshakalaka1 on 2019-05-30
OK, it looks like apt is working properly now!  I had to go through a few 'apt upgrade' and 'apt dist-upgrade' commands with some autoremoves, etc to get things into what seemed like a proper state.  I guess the do-release-upgrade failed part of the way through so it needed some follow package updates.  Anyways, should be all good now.  Thanks for your help, hopefully this will help some future Google searcher with a similar issue...

---

### Post by cruzer001 on 2019-05-30
Nicely done!

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

And welcome to the forums :D

---

