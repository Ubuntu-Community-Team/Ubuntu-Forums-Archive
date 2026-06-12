---
title: "apt-get question"
date: 2005-06-05
forum: General Help
---

### Post by Paul Panks on 2005-06-05
How do I use apt-get to update Ubuntu 5.04 with the latest packages from Firefox and other distributors?

Paul

---

### Post by Seti on 2005-06-05
In a console:```
sudo apt-get update
``` 
and ```
sudo apt-get -u dist-upgrade
``` 
will do it.

---

### Post by Paul Panks on 2005-06-05
Seems to work, but it said I needed "0" packages.

Paul

---

### Post by poofyhairguy on 2005-06-05
[QUOTE=Paul Panks]How do I use apt-get to update Ubuntu 5.04 with the latest packages from Firefox and other distributors?

Paul[/QUOTE]

Add the backports:

[http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

---

### Post by Majlo on 2005-06-05
If you want latest firefox gaim and others you must enable backport repository

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

Then type 
*sudo apt-get update* 
*sudo apt-get upgrade*

---

### Post by Seti on 2005-06-05
Yeah if I'm not mistaken then you're up to date.
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-dist-upgrade](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-dist-upgrade) applies to Ubuntu AFAIK, but I'm new here too lol!

Conversely you could just install the latest Firefox 1.0.4 from the official installer.

---

### Post by clarke.rainey on 2005-06-05
Well I also am trying to update firefox, but as of yesterday it gives me a 401 error when I try to connect to the repositories that have the newer version of firefox... and I have been able to connect to this repository in the past...

Did I miss an anouncement about that repository going down?..

```
Err http://backports.ubuntuforums.org hoary-backports/main mozilla-firefox-gnome-support 1.0.4~5.04ubp1+1.0.2-0ubuntu1
  401 Authorization Required
Err http://backports.ubuntuforums.org hoary-backports/main mozilla-firefox 1.0.4~5.04ubp1+1.0.2-0ubuntu1
  401 Authorization Required
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-backports/main/binary-i386/mozilla-firefox-gnome-support_1.0.4~5.04ubp1+1.0.2-0ubuntu1_i386.deb  401 Authorization Required
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-backports/main/binary-i386/mozilla-firefox_1.0.4~5.04ubp1+1.0.2-0ubuntu1_i386.deb  401 Authorization Required
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

---

### Post by mtron on 2005-06-05
[QUOTE=clarke.rainey]
Did I miss an anouncement about that repository going down?..[/QUOTE]

Yes you did...

see [here](http://ubuntuforums.org/showthread.php?t=37525) 

new Mirror for sources.list:

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

---

