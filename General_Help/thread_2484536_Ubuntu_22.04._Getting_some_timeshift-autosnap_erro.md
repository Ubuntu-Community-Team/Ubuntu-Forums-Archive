---
title: "Ubuntu 22.04. Getting some timeshift-autosnap errors during apt upgrade"
date: 2023-03-02
forum: General Help
---

### Post by Advait on 2023-03-02
I'm running Ubuntu 22.04 in VBox with btrfs on the root and home directories. timeshift-autosnap-apt is installed. Here's the output from the apt update command. See the timeshift-autosnap errors at the bottom of the code block. Anyway to fix this?

```
advait@advait-VirtualBox:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libflashrom1 libftdi1-2 libllvm13
Use 'sudo apt autoremove' to remove them.
The following packages have been kept back:
  fonts-opensymbol gir1.2-pango-1.0 gnome-remote-desktop libmm-glib0 libpango-1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0 libpangoxft-1.0-0
  libsnmp-base libsnmp40 modemmanager python3-software-properties software-properties-common software-properties-gtk
The following packages will be upgraded:
  evince evince-common libevdocument3-4 libevview3-3
4 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
Need to get 758 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://in.archive.ubuntu.com/ubuntu jammy-updates/main amd64 evince-common all 42.3-0ubuntu3 [130 kB]
Get:2 http://in.archive.ubuntu.com/ubuntu jammy-updates/main amd64 evince amd64 42.3-0ubuntu3 [301 kB]
Get:3 http://in.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libevdocument3-4 amd64 42.3-0ubuntu3 [179 kB]
Get:4 http://in.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libevview3-3 amd64 42.3-0ubuntu3 [149 kB]
Fetched 758 kB in 2s (339 kB/s)       
Rsyncing /boot into the filesystem before the call to timeshift.
Rsyncing /boot/efi into the filesystem before the call to timeshift.
Another instance of this application is running (PID=10648)
Unable to run timeshift-autosnap-apt! Please close Timeshift and try again. Script will now exit...
E: Problem executing scripts DPkg::Pre-Invoke '/usr/bin/timeshift-autosnap-apt'
E: Sub-process returned an error code
advait@advait-VirtualBox:~$ 

```

---

