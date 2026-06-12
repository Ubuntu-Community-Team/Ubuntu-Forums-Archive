---
title: "Error upgrading systemd package"
date: 2018-11-15
forum: General Help
---

### Post by Christopher_Thorn on 2018-11-15
Hi there,

I'm unable to upgrade systemd when running a [FONT=lucida console]full-upgrade[/FONT] on my system:

```
chris@hass ~ $ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libnss-systemd : Depends: systemd (= 237-3ubuntu10.6) but 237-3ubuntu10.4 is installed
 libpam-systemd : Depends: systemd (= 237-3ubuntu10.6) but 237-3ubuntu10.4 is installed
 systemd : Depends: libsystemd0 (= 237-3ubuntu10.4) but 237-3ubuntu10.6 is installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

So I try what it suggests, but it doesn't work:

```
chris@hass ~ $ sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  systemd
Suggested packages:
  systemd-container
The following packages will be upgraded:
  systemd
1 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
3 not fully installed or removed.
Need to get 0 B/2,894 kB of archives.
After this operation, 8,192 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 102461 files and directories currently installed.)
Preparing to unpack .../systemd_237-3ubuntu10.6_amd64.deb ...
Unpacking systemd (237-3ubuntu10.6) over (237-3ubuntu10.4) ...
dpkg: error processing archive /var/cache/apt/archives/systemd_237-3ubuntu10.6_amd64.deb (--unpack):
 unable to stat './usr/share/polkit-1/actions/org.freedesktop.hostname1.policy' (which I was about to install): Bad message
Errors were encountered while processing:
 /var/cache/apt/archives/systemd_237-3ubuntu10.6_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Does anyone have any suggestions as to what to do?

My system is: **Ubuntu 18.04.1 LTS (GNU/Linux 4.15.0-38-generic x86_64)**

Thanks for reading!

Chris

---

