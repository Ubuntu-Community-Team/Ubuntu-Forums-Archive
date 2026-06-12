---
title: "how can i uninstall current package and install an older one"
date: 2015-06-06
forum: General Help
---

### Post by au10tic on 2015-06-06
Im trying to remove network-manager version:**0.9.10.0-4ubuntu15** on lubuntu 15.04 'Vivid Vervet' this particular package seems to have problems connecting with openconnect using a .pem key. I've tried the same steps on 'lubuntu 14.02.2 LTS' and it works, that older version of lubuntu is using network-manager version: **0.9.8.8-0ubuntu7.1**

to remove it i have done ```
sudo apt-get remove network-manager
``` or ```
sudo apt-get --purge remove network-manager
``` but when i try to re-install the older version using a .deb file i downloaded off the internet it fails, below is the output when i run sudo dpkg -i /location/file.deb What am i doing wrong?

got the package from here: [HTML]http://packages.ubuntu.com/trusty/amd64/network-manager-gnome/download[/HTML]

output:
```
Selecting previously unselected package network-manager-gnome.(Reading database ... 105675 files and directories currently installed.)
Preparing to unpack network-manager-gnome_0.9.8.8-0ubuntu4_amd64.deb ...
Unpacking network-manager-gnome (0.9.8.8-0ubuntu4) ...
dpkg: dependency problems prevent configuration of network-manager-gnome:
 network-manager-gnome depends on libnm-gtk0 (= 0.9.8.8-0ubuntu4); however:
  Version of libnm-gtk0:amd64 on system is 0.9.10.1-0ubuntu4.
 network-manager-gnome depends on network-manager (>= 0.9.8); however:
  Package network-manager is not installed.
 libnm-gtk0:amd64 (0.9.10.1-0ubuntu4) breaks network-manager-gnome (<< 0.9.10.0) and is installed.
  Version of network-manager-gnome to be configured is 0.9.8.8-0ubuntu4.


dpkg: error processing package network-manager-gnome (--install):
 dependency problems - leaving unconfigured
Processing triggers for gconf2 (3.2.6-3ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.44.0-1ubuntu3) ...
Processing triggers for hicolor-icon-theme (0.14-0ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for mime-support (3.58ubuntu1) ...
Processing triggers for man-db (2.7.0.2-5) ...
Errors were encountered while processing:
 network-manager-gnome

```

---

### Post by ajgreeny on 2015-06-06
The problem is not anything wrong that you have done, it is simply that the version of network-manager that you are trying to install has version-specific dependencies that are not available in the repositories of vivid; this so called "dependency hell" is a problem of using a non standard version of any package and is one of the major reasons for sticking with repository versions of just about all the packagers available for the different versions of *ubuntu.

I can not help with any answer to your problem, only the explanation, but I wonder if it might be better for you to go back to 14.04 which still has years of support left and is as stable a versiion as I can remember in my 10 years of using Ubuntu; must you use VV for other reasons which stop 14.04 being any use to you?

---

### Post by au10tic on 2015-06-10
Thanks for the response ajgreeny, i just wanted to be running on the latest, but suddenly vpn started working. What i did differently was re-install the OS then installed openconnect via openconnect network-manager-openconnect-gnome restarted network-manager and now it connects using my .pem key which is what i needed.

---

