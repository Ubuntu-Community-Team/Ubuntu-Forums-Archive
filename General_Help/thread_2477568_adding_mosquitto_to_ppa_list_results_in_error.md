---
title: "adding mosquitto to ppa list results in error"
date: 2022-07-29
forum: General Help
---

### Post by eelie on 2022-07-29
Hi! 

I'd like to add Mosquitto to my list of updates when I run [COLOR=#333333]sudo apt update, but I get these errors when running this on Ubuntu 22.04.


[/COLOR]
[LIST]
[*]sudo apt-add-repository ppa:mosquitto-dev/mosquitto-ppa
[*]sudo apt-get update
[/LIST]
[COLOR=#333333]
I eventually deleted it from the list

[/COLOR]/etc/apt/sources.list

so that the message doesn't appear everytime I update the system, but how do I update mosquitto now by including it on my list?

thanks


```
an@GC676AA-ABA-m8150n:~$ sudo apt-add-repository ppa:mosquitto-dev/mosquitto-ppa
PPA publishes dbgsym, you may need to include 'main/debug' component
Repository: 'deb https://ppa.launchpadcontent.net/mosquitto-dev/mosquitto-ppa/ubuntu/ jammy main'
More info: https://launchpad.net/~mosquitto-dev/+archive/ubuntu/mosquitto-ppa
Adding repository.
Press [ENTER] to continue or Ctrl-c to cancel.^[[A
Adding deb entry to /etc/apt/sources.list.d/mosquitto-dev-ubuntu-mosquitto-ppa-jammy.list
Adding disabled deb-src entry to /etc/apt/sources.list.d/mosquitto-dev-ubuntu-mosquitto-ppa-jammy.list
Adding key to /etc/apt/trusted.gpg.d/mosquitto-dev-ubuntu-mosquitto-ppa.gpg with fingerprint 77B7346A59027B33C10CAFE35E64E954262C4500
Hit:1 http://ca.archive.ubuntu.com/ubuntu jammy InRelease
Hit:2 http://security.ubuntu.com/ubuntu jammy-security InRelease
Hit:3 https://repos.influxdata.com/debian stable InRelease
Hit:4 http://ca.archive.ubuntu.com/ubuntu jammy-updates InRelease
Hit:5 http://ca.archive.ubuntu.com/ubuntu jammy-backports InRelease
Ign:6 https://ppa.launchpadcontent.net/mosquitto-dev/mosquitto-ppa/ubuntu jammy InRelease
Err:7 https://ppa.launchpadcontent.net/mosquitto-dev/mosquitto-ppa/ubuntu jammy Release
  404  Not Found [IP: 185.125.190.52 443]
Reading package lists... Done
E: The repository 'https://ppa.launchpadcontent.net/mosquitto-dev/mosquitto-ppa/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

---

### Post by QIII on 2022-07-29
You may have to contact the maintainer of the PPA (Personal Package Archive).  It does not appear that they have made a package for 22.04 available in their archive.  There is nothing we can do about that for you.

---

### Post by eelie on 2022-07-29
that is what I thought. I will contact them (or at least) I will try to do so.

thank you for your reply.

---

