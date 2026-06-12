---
title: "[SOLVED] Can't open synaptic / update manager"
date: 2007-09-19
forum: General Help
---

### Post by stinkinrich88 on 2007-09-19
Hello,

everytime I try to open synaptic I get:

```
E: The package qmpdclient needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```

(and everytime I try to apt-get something)

update manager:

> An unresolvable problem occurred while initialising the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package qmpdclient needs to be reinstalled, but I can't find an archive for it.'

add / remove is fine.

When I try to uninstall qmpdclient with aptitude, I also get an error. I've managed to install qmpdclient and get it working again with make install, however, I still can't use apt-get etc

Any ideas? thank you!!

---

### Post by tszanon on 2007-09-19
> **stinkinrich88 said:**
> Hello,

everytime I try to open synaptic I get:

```
E: The package qmpdclient needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```

(and everytime I try to apt-get something)

update manager:



add / remove is fine.

When I try to uninstall qmpdclient with aptitude, I also get an error. I've managed to install qmpdclient and get it working again with make install, however, I still can't use apt-get etc

Any ideas? thank you!!
Have you tried using apt-get (or dpkg) to remove that package?

---

### Post by stinkinrich88 on 2007-09-20
sorry! forgot to subscribe!! 

apt-get wouldn't let me do anything, aptitude kept breaking everytime I tried to do anything to qmpdclient. 

Anyway, dpkg was what I was looking for! thanks!

SOLUTION:

```
sudo dpkg --remove --force-remove-reinstreq qmpdclient
```

where 'qmpdclient' is the package that's being annoying. 

solution found: [http://www.ubuntugeek.com/package-installation-error-and-solution.html#more-35]("http://www.ubuntugeek.com/package-installation-error-and-solution.html#more-35")

---

### Post by tszanon on 2007-09-20
Good to know your problem is solved!
Please, edit the thread and mark it as SOLVED, so everyone can benefit from it.

---

### Post by stinkinrich88 on 2007-09-20
oh cool! didn't know you could do that! thanks!

---

