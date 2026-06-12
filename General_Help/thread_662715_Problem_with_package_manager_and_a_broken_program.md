---
title: "Problem with package manager and a broken program"
date: 2008-01-09
forum: General Help
---

### Post by atsoupaletos on 2008-01-09
Drupal is broken and when i try to install any software on my system(Kubuntu Gutsy), it tries to remove it. But errors encounter during this operation and nothing installs. I've tried apt-get, synaptic and adept. This is what apt-get -install 'name of program' returns:
 
[COLOR="Lime"]lampros@atsoupaletos:~$ sudo apt-get install xchat
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libenchant1c2a libsexy2 xchat-common
Suggested packages:
  libnet-google-perl
Recommended packages:
  libnotify-bin
The following packages will be REMOVED:
  drupal
The following NEW packages will be installed:
  libenchant1c2a libsexy2 xchat xchat-common
0 upgraded, 4 newly installed, 1 to remove and 63 not upgraded.
1 not fully installed or removed.[/COLOR]

and after trying to install returns:

[COLOR="Lime"]Removing drupal ...
dpkg: error processing drupal (--remove):
 subprocess post-removal script returned error exit status 10
Errors were encountered while processing:
 drupal
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/COLOR]
Any suggestions?

---

### Post by -grubby on 2008-01-09
perhaps 
```
sudo apt-get remove drupal
```
or if that doesn't work
```
sudo apt-get install -f
```
EDIT:
PS could you please use the  tags around your text instead of highlighting it green (it's hard to read)

---

### Post by atsoupaletos on 2008-01-10
It still returns the same error with both commands.

---

