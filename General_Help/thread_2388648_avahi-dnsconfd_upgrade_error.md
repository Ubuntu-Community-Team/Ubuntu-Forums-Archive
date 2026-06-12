---
title: "avahi-dnsconfd upgrade error"
date: 2018-04-05
forum: General Help
---

### Post by valvegrid on 2018-04-05
Using Synaptic to upgrade today and everything went fine until it got to upgrading avahi-dnsconfd, I tried upgrading from the terminal as well but got the same result.

```
Gtk-WARNING **: Theme directory  of theme default.kde4 has no size field(Reading database ... 304876 files and directories currently installed.)
Preparing to unpack .../avahi-dnsconfd_0.6.32~rc+dfsg-1ubuntu2.1_amd64.deb ...
Job for avahi-daemon.socket canceled.
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
Job for avahi-daemon.socket canceled.
dpkg: error processing archive /var/cache/apt/archives/avahi-dnsconfd_0.6.32~rc+dfsg-1ubuntu2.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/avahi-dnsconfd_0.6.32~rc+dfsg-1ubuntu2.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```

This is my system:

```
Release 16.04.4 LTS (Xenial Xerus) 64-bitKernel Linux 4.13.0-38-generic x86_64
MATE 1.12.1
Processor: Intel® Celeron(R) CPU N3450 @ 1.10GHz × 4 
Memory: 3.7GiB
```

I've blocked it from installing at the moment because I suspect it's a bug and the system is running OK without the upgrade, unless anyone knows otherwise. I did check the forum to see if this has occurred before and I can't see any reference to is at all.

So any ideas on what it might be please?

Additionally I found this from a couple of years ago which exactly the same as I'm getting, could it be a re-occurrence?

[https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/1563945](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/1563945)

---

### Post by cruzer001 on 2018-04-05
Possibility the package is corrupted.

```
sudo rm /var/cache/apt/archives/avahi-dnsconfd_0.6.32~rc+dfsg-1ubuntu2.1_amd64.deb
```

Remove the block then update and upgrade.

---

### Post by valvegrid on 2018-04-05
Thanks, tried that, it's still the same.

---

### Post by linuxinside on 2018-04-05
Got the same error today.

Fixed it with:
```

sudo systemctl disable avahi-daemon
sudo apt update && sudo apt upgrade
sudo systemctl enable avahi-daemon

```

Finally reboot the system.

---

### Post by valvegrid on 2018-04-05
Many thanks, that fixed it, I learn something every day.

---

### Post by pogonici on 2018-04-06
Thank you!

---

### Post by dirx on 2018-04-08
Thank you!

---

### Post by mspeers on 2018-05-11
Thank you. Fix the issue for me\\:D/

---

