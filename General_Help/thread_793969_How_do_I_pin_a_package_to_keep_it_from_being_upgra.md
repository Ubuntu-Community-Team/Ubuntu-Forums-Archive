---
title: "How do I pin a package to keep it from being upgraded?"
date: 2008-05-14
forum: General Help
---

### Post by jakev383 on 2008-05-14
I have a custom built postfix package that I have installed and running.  When I do a apt-get upgrade it wants to upgrade the postfix package to a newer version, but I don't want that.
How would I pin the package to keep it from being updated? I'd tried "aptitude hold postfix" and adding it to /etc/apt/preferences:
```

Package: postfix
Pin: version 2.3.8-2
Pin-Priority: -1

Package: postfix-mysql
Pin: version 2.3.8-2
Pin-Priority: -1

```
(I also tried leaving the Pin-Priority line out to no effect).
I do not have the GUI installed, so I cannot lock the package in Synaptic.
Thanks in advance!

---

### Post by jakev383 on 2008-05-14
Ahh. Found the answer on a Debian site.  To pin my version of postfix:
```
echo postfix hold | dpkg --set-selections
```
It still shows when I run "apt-get upgrade", but even when I perform a dist-upgrade it does not upgrade that package.
Hope that helps someone else too!

---

### Post by nick_h on 2008-05-14
This functionality is also available via the Synaptic package manager using Package->Lock Version.

---

### Post by disturbedite on 2008-05-14
i was gonna mention what nick_h said, but he beat me to it.  i don't think there is a way to do this with adept though...

---

