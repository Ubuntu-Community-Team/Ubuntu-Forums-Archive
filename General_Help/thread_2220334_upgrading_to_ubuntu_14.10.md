---
title: "upgrading to ubuntu 14.10"
date: 2014-04-27
forum: General Help
---

### Post by quamirichie on 2014-04-27
i am using ubuntu 13.10 to 14.10

---

### Post by TheFu on 2014-04-27
You'll need to go through 14.04 and wait until October for 14.10.

---

### Post by quamirichie on 2014-04-27
how do i get upgrade for 14.04

---

### Post by TheFu on 2014-04-27
```
sudo aptitude update
sudo aptitude full-upgrade
reboot
# Make a 100% recoverable backup - however you normally do it.
sudo do-release-upgrade

```
Ensure your system is currently patched before starting. That's what the first 3 commands do.  Make a backup of everything you do not want to loose. Bad things sometimes happen during major updates. DO NOT SKIP THIS.

---

### Post by kansasnoob on 2014-04-27
[https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes#Upgrading_from_Ubuntu_13.10](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes#Upgrading_from_Ubuntu_13.10)

---

