---
title: "&quot;apt-get-update&quot; doesn't recognize new sources ?"
date: 2012-10-20
forum: General Help
---

### Post by trinhanhngoc on 2012-10-20
[IMG]http://img708.imageshack.us/img708/3887/sourcesl.png[/IMG]

i have some new sources but *apt-get-update* doesn't recognize it... and i cann't install new packages.

[IMG]http://img202.imageshack.us/img202/4237/aptgetupdate.png[/IMG]

---

### Post by Cheesemill on 2012-10-20
Looks OK to me, you can see the PPA's you've added in your output.

What errors do you get when trying to install packages?

---

### Post by trinhanhngoc on 2012-10-20
```
trinhanhngoc@nntforever:~$ sudo apt-get install classicmenu-indicator
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package classicmenu-indicator
```

---

### Post by Cheesemill on 2012-10-20
The guy that runs the PPA for classicmenu-indicator hasn't updated the PPA for 12.10 yet, you'll have to wait until he does (12.10 has only been out for 2 days).

Alternatively you could download the version for 12.04 directly and see if it still works with 12.20 although it isn't guaranteed.
[https://launchpad.net/~diesch/+archive/testing/+files/classicmenu-indicator_0.07_all.deb](https://launchpad.net/~diesch/+archive/testing/+files/classicmenu-indicator_0.07_all.deb)

---

### Post by mc4man on 2012-10-20
When adding a ppa you could check the page, (Filtered if need be) to see whats avail.
Ex. - only 2 here for 12.10
[https://launchpad.net/~diesch/+archive/testing?field.series_filter=quantal](https://launchpad.net/~diesch/+archive/testing?field.series_filter=quantal)

Or install/open synaptic, click on the "Origin" tab, highlight the ppa, it will list all available/installed packages from the source selected, screen example for gnome3 ppa

---

### Post by trinhanhngoc on 2012-10-20
thank you so much

---

