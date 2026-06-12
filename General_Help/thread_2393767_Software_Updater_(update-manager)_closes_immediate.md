---
title: "Software Updater (update-manager) closes immediately"
date: 2018-06-07
forum: General Help
---

### Post by Erik1984 on 2018-06-07
I'm running Ubuntu Mate 18.04 Bionic Beaver (upgraded from 17.10).

This happens for a while now. Occasionally the Software Updater opens and shows me updates but most of the time not. Software Updater often appears in the taskbar, probably because there are pending updates, but cannot be opened (the window won't show and it disappears from the task bar again). Opening it manually from the menu (System > Administration > Software Updater) also fails.

Starting from the terminal yields the same result. Program opens but closes quickly without showing a window.
```
update-manager
```

Sadly the terminal reports no errors or other useful information, the command returns exit code 0.

Here is my sources.list without commented out lines:
```

deb http://nl.archive.ubuntu.com/ubuntu/ bionic main restricted
deb http://nl.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
deb http://nl.archive.ubuntu.com/ubuntu/ bionic universe
deb http://nl.archive.ubuntu.com/ubuntu/ bionic-updates universe
deb http://nl.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://nl.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
deb http://nl.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse

```

Updating with
```
sudo apt update && sudo apt upgrade
```
Works fine.

Any ideas?

---

### Post by Erik1984 on 2018-06-13
Bump, but an informational one ;)

My guess now is that this is an authorization issue. Software Updater did not start, as described in the first post. But it worked fine when starting with the following command
```
pkexec env DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY update-manager
```

Although this should not be necessary / is undesirable. Anyone else had a similar issue with the Software Updater once?

---

### Post by robelli on 2018-06-15
I am running Ubuntu 18.04 Mate and ever since I installed it I am having the same problem . The updater tells me it has updates (84Mb to download). It starts to download and then just disappears off the screen with no updates having taken place . So what this means although there are updates available the updater does not carry out its function and leaves my OS with nil updates having been carried out . Not very good I would suggest.

---

### Post by Erik1984 on 2018-06-19
Somehow the Software Updater seems to work again, but not completely. It doesn't show all available updates. Running **apt update** and **apt list --upgradable** shows 3 packages to update. Software Updater says the system is up to date. Maybe it looks at a different sources list than apt. The source of the listed updates is bionic-updates and that is also checked under the Updates tab in Software & Updates.

---

### Post by bodhin2 on 2018-06-19
i asked the question last week about running software updater and also doing the aptu pdate and dist-upgrade.  i get similar stuff.  software updater says computer is upt to date. you run apt update and then apt dist-upgrade and it finds more stuff to install/update/upgrade.  people gave me legit honest answers; however i could not understand the weird anomalies.  happened yesterday and i believe the day before across 3 laptops.  i believe i will stick with the terminal commands like l have been doing the last year with another distro prior to coming to ubuntu.  i scratch my head a bit but live with it.

---

