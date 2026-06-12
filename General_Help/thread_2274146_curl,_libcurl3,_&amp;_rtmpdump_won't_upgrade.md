---
title: "curl, libcurl3, &amp; rtmpdump won't upgrade"
date: 2015-04-18
forum: General Help
---

### Post by mdavis1231 on 2015-04-18
curl, libcurl3, & rtmpdump are showing in Synaptic Package Manager as being upgradable, but they won't upgrade.  If I try to remove them, it says that it will also remove my Virtualbox 4.3 & Whoopsie.  If I try to upgrade them, it says that libcurl3 & rtmpdump are "broken dependencies".  How do you fix this? ](*,)

---

### Post by dino99 on 2015-04-18
if you are using 'extra' sources, like ppa, then you possibly met a conflict. Try to downgrade these packages if they seem being a direct/indirect dependencies of curl and the like.

note: if you are using xubuntu/kubuntu, devs are still fixing lot of bugs; so wait for a fix for these curl packages.

---

### Post by mc4man on 2015-04-18
simulate (-s) an upgrade, see how that goes
```
sudo apt-get -s dist-upgrade
```

---

### Post by mdavis1231 on 2015-04-18
Nothing is working.  I didn't realize before now and I've been using Ubuntu since 8.04 LTS that apparently it's very important to keep track of what PPA's are in your system, and to know exactly what each one is for so that you can troubleshoot should something like this happen.  I guess my only recourse is to start with a fresh install and only put in the PPA's that I need instead of importing them from 12.04 LTS.  I've probably got over 30 PPA's in my Software Sources, so it would be virtually impossible for me to pinpoint exactly what caused this so that I can fix it.  I guess I've learned a valuable lesson!

---

### Post by ian-weisser on 2015-04-18
> **mdavis1231 said:**
> I guess my only recourse is to start with a fresh install and only put in the PPA's that I need instead of importing them from 12.04 LTS.  I've probably got over 30 PPA's in my Software Sources, so it would be virtually impossible for me to pinpoint exactly what caused this so that I can fix it.

It's fixable.
A bit tedious, but not difficult at all.

One method is to disable all the PPAs, and to re-enable those you need as you discover the need.
Another method is to use bisection - disable half the PPAs, and see if that solves the problem. And the to bisect that half.
Plenty of other methods.

Remember that there is a difference between disabling the PPA (which leaves the PPA software on your system) and uninstalling the PPA software (which leaves the PPA enabled). To resolve a conflict, you might need to disable the PPA *and* uninstall the software...and then install the Ubuntu repository version of that software.

---

