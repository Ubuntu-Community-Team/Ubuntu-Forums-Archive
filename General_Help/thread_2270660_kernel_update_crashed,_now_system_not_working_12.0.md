---
title: "kernel update crashed, now system not working 12.04 LTS"
date: 2015-03-24
forum: General Help
---

### Post by stkeg on 2015-03-24
my 12.04 LTS was updating this morning but crashed while upgrading the kernel.

now the system doesn't work properly (doesn't go into GUI or no shell login)

i'm guessing the update didn't finish?

i am able to remote ssh into the machine from a different machine and i have a shell. tried sudo apt-get update and upgrade, but the machine thinks everything is up to date.

do i need to force upgrade of the last kernel? how would i do that?

or is there something else i need to do to fix this?

---

### Post by v3.xx on 2015-03-24
'Apt-get upgrade' will not upgrade the kernel.  You can do a dist-upgrade for the kernel.
```
sudo apt-get dist-upgrade
```
[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

You can also try repair commands.
```
sudo dpkg --configure -a #used to complete a unconfigured package
```
and
```
sudo apt-get -f install #attempt to fix broken packages
```

---

