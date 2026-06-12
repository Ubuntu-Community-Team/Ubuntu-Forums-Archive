---
title: "Conflicting version information"
date: 2021-02-24
forum: General Help
---

### Post by Frank P on 2021-02-24
I just recently upgraded from 18.04LTS desktop to 20.04 LTS desktop using apt do-release-upgrade.
Checking "Details" from gnome shows 20.04LTS; using ssh from another pc says "welcome to Ubuntu 18.04 LTS ..............."
Anyone know what might be wrong and if it's a problem?
Thanks
Frank

---

### Post by TheFu on 2021-02-24
What does **lsb_release -a** say?
Anything else would be cosmetic, IMHO.

---

### Post by Frank P on 2021-02-25
lsb_release -a
```

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.2 LTS
Release:    20.04
Codename:    focal

```

so i guess everything is okay then

Frank

---

### Post by TheFu on 2021-02-25
You could look through the installed packages for any with "18.04" in the package filename.
```
dpkg -l "*18.04*"
```
Sometimes old versions will be left behind. Be careful swapping in newer versions.

---

### Post by Frank P on 2021-02-25
Here's the output
```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                               Version      Architecture Description
+++-==================================================-============-============-=================================
un  oem-config-frontend-18.04.14.1timbuktu2somerville1 <none>       <none>       (no description available)

```

Is it meaningful
Thanks
Frank

---

