---
title: "how to check system requirments and drivers"
date: 2012-10-30
forum: General Help
---

### Post by yasirmahmood on 2012-10-30
hey guys I'm using Ubuntu 12.10 and i want to ask you in Ubuntu how do we check our system requirements and drivers details as we do in window this way
my computer>right click> properties
and everything is there except for VGA driver detail and in device manager we can see installed drivers how do we find these things in Ubuntu ..
please reply thanks in advance :)

---

### Post by codemaniac on 2012-10-30
> **yasirmahmood said:**
> hey guys I'm using Ubuntu 12.10 and i want to ask you in Ubuntu how do we check our system requirements and drivers details as we do in window this way
my computer>right click> properties
and everything is there except for VGA driver detail and in device manager we can see installed drivers how do we find these things in Ubuntu ..
please reply thanks in advance :)

I generally use command line tools to extract various pieces of system information.


see the below link .
[https://help.ubuntu.com/10.04/basic-commands/C/sys-info-commands.html](https://help.ubuntu.com/10.04/basic-commands/C/sys-info-commands.html)

[http://en.wikipedia.org/wiki/Procfs](http://en.wikipedia.org/wiki/Procfs)

In addition i also use dmidecode sometimes.
see man dmidecode.

e.g. the below would show information about your bios.

```
sudo dmidecode --type bios
```

---

### Post by cmcanulty on 2012-10-30
sysinfo is an easy graphical way

---

### Post by jerrrys on 2012-10-30
also HardInfo

[https://help.ubuntu.com/community/HardInfo](https://help.ubuntu.com/community/HardInfo)

---

### Post by cmcanulty on 2012-10-30
wow that's a lot better than sysinfo thanks

---

### Post by Mark Phelps on 2012-10-30
Just be aware that sysinfo has a known history of misreporting the video driver info.  Lots of people come here complaining that it says "unknown", presuming they have NO video driver installed -- when, in fact, they DO have the proper driver installed by default.

Linux is NOT Windows -- you don't follow an installation/upgrade by immediately hunting around for new drivers.  Linux scans your hardware, downloads the drivers, and installs them for you -- automatically.

---

### Post by yasirmahmood on 2012-10-30
bundle of Thanks guys it really helped much obliged :))

---

