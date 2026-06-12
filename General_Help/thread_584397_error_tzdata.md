---
title: "error tzdata"
date: 2007-10-20
forum: General Help
---

### Post by RuB3N on 2007-10-20
im trying to install a package but this pops up when it trys to install.

---

### Post by por100pre1 on 2007-10-21
Please read [this]("https://bugs.launchpad.net/ubuntu/gutsy/+source/tzdata/+bug/116193").

---

### Post by wjhildreth on 2007-10-23
I have change the timezone and tried to reconfigure tzdata but it does not work work for me.  :-(

Joe

---

### Post by halfB on 2007-10-26
Looks like there are a bunch of us with this tzdata problem that changing timezones did not help.  I am also stuck. Sure do not want to do a fresh install.
HalfB

---

### Post by Sir_Yaro on 2007-10-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/gutsy/+source/tzdata/+bug/116193](https://bugs.launchpad.net/ubuntu/gutsy/+source/tzdata/+bug/116193) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				[COLOR="red"]**_do it as a root:_**[/COLOR]
```
dpkg -P --force-depends tzdata; echo -e 'y\n2\nArgentina/Buenos_Aires' | dpkg -i tzdata_2007f-0ubuntu0.7.4_all.deb
```
```
dpkg -i tzdata_2007h-0ubuntu0.7.10_all.deb
```
for a packages look here:
[http://mirror.ne.gov/ubuntu/pool/main/t/tzdata/](http://mirror.ne.gov/ubuntu/pool/main/t/tzdata/)

it works for me :guitar:

---

### Post by Mr_bleu on 2007-11-24
I installed NTP and it fixed the tzdata error.  The problem arose when I had uninstalled it.

---

### Post by OzzyFrank on 2007-12-16
I only just got this, and couldn't install anything else as the error kept popping up. Looked around and saw a lot of mention of changing the time zone to other places like Berlin. I was going to do that via the Time & Date app and noticed the zone had somehow been set to nothing. For me setting it to my own locale fixed it. Cheers

---

