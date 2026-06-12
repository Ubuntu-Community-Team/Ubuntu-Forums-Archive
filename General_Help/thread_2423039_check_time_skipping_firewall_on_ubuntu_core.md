---
title: "check time skipping firewall on ubuntu core"
date: 2019-07-16
forum: General Help
---

### Post by matteoraggi on 2019-07-16
Hi, on raspbian I am using htpdate to check the time by the web skipping the firewalls, how to do the same with ubuntu core?

---

### Post by #&amp;thj^% on 2019-07-16
If your using an Ubuntu OS 16.04 or higher:
```
timedatectl
```
Should work.

---

### Post by matteoraggi on 2019-07-16
thanks, but how to install it into ubuntu core if there is not a snap?
[https://snapcraft.io/search?q=timedatectl](https://snapcraft.io/search?q=timedatectl)
Maybe timedatectl that normally is included into ubuntu, then it is included also into ubuntu core too?

---

### Post by uRock on 2019-07-16
You should be able to install it with,
```
sudo apt install timedatectl
```

---

### Post by matteoraggi on 2019-07-16
sorry, sudo apt will not work on Ubuntu Core.
there is no apt
apt command not found

---

### Post by deadflowr on 2019-07-17
You can install apt/apt-get with the classic snap package
see: [https://askubuntu.com/a/925505]("https://askubuntu.com/a/925505")

timedatectl is actually a part of the systemd package and infrastructure, fwiw.
(Almost all the somethingCTL commands are systemd. systemctl, loginctl, timedatectl : all in the systemd package)

But you might check further through the available snap packages using snap commands like find and search.
There may be a ready made tool for what you want already in there.

---

### Post by matteoraggi on 2019-07-17
Well the system says the classic snap is not available for 18.

---

### Post by #&amp;thj^% on 2019-07-17
Are you sure?
```
snap info classic
name:      classic
summary:   Classic environment
publisher: Canonical&#10003;
contact:   snaps@canonical.com
license:   Other Open Source
description: |
  Classic environment
snap-id: <Snip by OP>
channels:
  stable:       &#8211;                              
  candidate:    &#8211;                              
  beta:         (26)  4kB devmode
  edge:         16.04     2018-10-19 (42) 12kB devmode
  18/stable:    &#8211;                              
  18/candidate: &#8211;                              
  18/beta:      18.04-0.1 2019-07-05 (37) 31MB devmode
  18/edge:      18.04-0.1 2018-10-19 (37) 31MB devmode

```
Also if you could define your posts to include the information on your usage. (Specs, And if on a PI or not) to help us not lead you down an endless road of suggestions.

---

### Post by matteoraggi on 2019-07-17
the classic snap does not appear to be working on 18.04 Core at all. I have tried all of the suggestions already
root@localhost:~# snap info classic
name:      classic
summary:   Classic environment
publisher: Canonical&#10003;
contact:   [email]snaps@canonical.com[/email]
license:   Other Open Source
description: |
  Classic environment
snap-id: QbSFwGGAgvG8zHl9nWLY7vEee8lhgFsp
channels:
  stable:    &#8211;                          
  candidate: &#8211;                          
  beta:      16.04 2017-08-17 (26)  4kB devmode
  edge:      16.04 2018-10-19 (42) 12kB devmode
root@localhost:~#

---

### Post by #&amp;thj^% on 2019-07-17
I'm still unclear, how is it not working?
Take your time and give us all the information you can.
```
snap list
Name     Version    Rev   Tracking  Publisher   Notes
classic  16.04      
26    beta      canonical&#10003;  devmode
core     16-2.39.3  7270  stable    canonical&#10003;  core

```
Also can you show the exact command used to install it.
maybe just a guess you mean you can't install it.
Here is what i used:
```
snap install beta classic --devmode

```
And:
```
sudo snap refresh classic --channel=beta
snap "classic" has no updates available
```
now:
```
sudo classic
Creating classic environment
Parallel unsquashfs: Using 4 processors
11392 inodes (12613 blocks) to write

[===========================================================-] 12613/12613 100%

created 8909 files
created 1441 directories
created 2394 symlinks
created 79 devices
created 0 fifos

```
Now for apt:
```
snap search apt
Name         Version             Publisher      Notes    Summary
loopchain    2.2.1               loopchain      -        loopchain
egmde        86-mir1.3.0-snap60  alangriffiths  classic  Try Mir as your desktop, or as a window on your desktop
nano-strict  4.0+pkg-b7b9        brlin          -        Small, friendly text editor (Strict Confinement)
tree         1.8.0+pkg-3fd6      brlin          -        A directory listing command that produces a depth indented listing of files

```
BTW This is>>```
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 19.04
Release:	19.04
Codename:	disco

```
Also from one of Devs:
> Allowing access to timedatectl at all times seems fine since this is just a client. Then, we can allow access to the relevant DBus objects and methods when the respective interfaces are connected (time-control, timezone-control, etc).

We also shouldn&#8217;t require a special interface to read the time, but I assume that&#8217;s already the case?
[https://github.com/snapcore/snapd/pull/3364](https://github.com/snapcore/snapd/pull/3364)

---

