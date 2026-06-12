---
title: "GDM fails on boot, works when ran manually"
date: 2015-11-18
forum: General Help
---

### Post by PrinceVince on 2015-11-18
Yersterday I installed fglrx-updates as I need the proprietary driver for a program I use. After doing so, GDM stopped working on bootup. It popus up for a tenth of a second, then the screen goes and stays black and doesn't respond to keyboard actions. I can switch to tty1 though and if I log in from there, I can do **sudo systemctl start gdm.service** just fine; likewise **startx** gets me into the GNOME shell without issues. I have removed fglrx again (it has its own issues) to the best of my abilities and reverted to the open source driver, but the failure on bootup remains.

I tried reinstalling the xorg related packages and also running **sudo dpkg-reconfigure xserver-xorg** but to no avail. My /etc/X11/ contains no *xorg.conf*.

There are no Xorg logs in */var/log/* after bootup, but when I start the gdm service manually as described above, I get the following: [Xorg.0.log]("http://paste.ubuntu.com/13333395/") and [Xorg.0.log.old]("http://paste.ubuntu.com/13333400/").

I think it might have something to do with user rights, but I'm out of ideas on how to approach this further.

Ubuntu 15.10, GNOME 3.18

---

### Post by PrinceVince on 2015-11-19
**Edit:** Below package was found under the name **xserver-xorg-core/wily-proposed** but did not solve the problem.

I'm thinking [this bug]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1237904") might be behind my issue.

Comment #24 reads:
> Accepted xorg-server into wily-proposed. The package will build now and be available at [https://launchpad.net/ubuntu/+source/xorg-server/2:1.17.2-1ubuntu9.1](https://launchpad.net/ubuntu/+source/xorg-server/2:1.17.2-1ubuntu9.1) in a few hours, and then in the -proposed repository.
This was about a week ago. I followed [this guide]("https://wiki.ubuntu.com/Testing/EnableProposed") to enable wily-proposed, including the pinning to avoid package updates across the board.

I then tried to install **xserver-xorg**, which to my understanding is the binary package corresponding to[ xorg-server]("https://launchpad.net/ubuntu/+source/xorg-server/2:1.17.2-1ubuntu9.1")-source:
```

sudo apt-get update # showed wily-proposed being fetched
sudo apt-get install xserver-xorg/wily-proposed

```
...which yields:
```

E: Release 'wily-proposed' for 'xserver-xorg' was not found

```
Could someone point me to the correct package/command? Thanks.

---

