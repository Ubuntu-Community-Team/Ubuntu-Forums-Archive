---
title: "After Update to 22.04, Updates are held back. Why?"
date: 2022-09-24
forum: General Help
---

### Post by ne29914 on 2022-09-24
The headline and this should say all:
```
macro@macro6910p:~$ sudo myupgrade
[sudo] password for macro: 
Hit:1 http://ppa.launchpad.net/kicad/kicad-6.0-releases/ubuntu jammy InRelease
Hit:2 https://brave-browser-apt-release.s3.brave.com stable InRelease                                                       
Hit:3 http://archive.ubuntu.com/ubuntu jammy InRelease                                                                      
Hit:4 http://archive.ubuntu.com/ubuntu jammy-updates InRelease
Hit:5 http://archive.ubuntu.com/ubuntu jammy-security InRelease
Hit:6 http://archive.ubuntu.com/ubuntu jammy-backports InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
9 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libnss-systemd libpam-systemd libspeechd2 libsystemd0 libudev1 systemd systemd-sysv systemd-timesyncd udev
0 to upgrade, 0 to newly install, 0 to remove and 9 not to upgrade.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 9 not to upgrade.
macro@macro6910p:~$ 

```
I never had this on 20.04. What's up here?

("myupgrade" is just a small script with apt opdate, apt upgrade, apt autoremove)

---

### Post by Bashing-om on 2022-09-24
ne29914; Hello.

One phrase: - phased updates :D

See: 
[https://wiki.ubuntu.com/TimeBasedReleases](https://wiki.ubuntu.com/TimeBasedReleases)

and >>
[http://people.canonical.com/~ubuntu-archive/phased-updates.html](http://people.canonical.com/~ubuntu-archive/phased-updates.html)

Here shows that systemd has been rolled back. Wait for the fix and the updates to continue.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by ne29914 on 2022-09-25
Thanks, @Bashing-om
Is this new to 22.04? I cannot recall having this issue with 20.04.

---

### Post by &amp;KyT$0P# on 2022-09-25
> **ne29914 said:**
> Is this new to 22.04? I cannot recall having this issue with 20.04.

It was [introduced in 21.04]("https://discourse.ubuntu.com/t/phased-updates-in-apt-in-21-04/20345").

---

### Post by ne29914 on 2022-09-25
Thanks @halogen2, I understand the issue now, good link..

Most idiotic "improvement" i've seen to date, and apparently only good for the developers. Somewhat like snap.
But OK, now I know; only 99% of other Ubuntu users don't know and are looking for APT/PPA problems. Great idea! Great execution!
How about a little text after "...held back" saying "will be upgraded later when ready"? Just a suggestion.

---

### Post by ian-weisser on 2022-09-25
> **halogen2 said:**
> It was [introduced in 21.04]("https://discourse.ubuntu.com/t/phased-updates-in-apt-in-21-04/20345").

It was indeed introduced to apt in 21.04. But it was introduced to Update Manager a decade ago. It's not new.


> **ne29914 said:**
> How about a little text after "...held back" saying "will be upgraded later when ready"? Just a suggestion.

Apt is Open Source. Contributions of code to improve everybody's experience are welcome.

---

### Post by &amp;KyT$0P# on 2022-09-25
> **ne29914 said:**
> Thanks @halogen2.

You're welcome.

> Most idiotic "improvement" i've seen to date, and apparently only good for the developers.

I would disagree.  For me, as a user, it's a genuine improvement: now I can finally sync all my systems to phase into updates exactly the same, without having to "fake it" via manual fiddling at almost every update.

But, +1 that it needs to be clearer when a held back update is because it's phased.

---

### Post by ne29914 on 2022-09-25
OK. understood. It's a great thing for sysadms.
I'll mark this as solved.

---

