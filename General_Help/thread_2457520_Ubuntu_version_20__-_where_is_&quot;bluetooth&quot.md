---
title: "Ubuntu version 20  - where is &quot;bluetooth&quot; setting / manager ?"
date: 2021-02-03
forum: General Help
---

### Post by anneranch on 2021-02-03
See title

---

### Post by wildmanne39 on 2021-02-03
*Thread moved to **General Help for a more appropriate fit**.*

---

### Post by guiverc on 2021-02-03
Please be specific with release details.

Ubuntu has different products, the *year.month* format is used for standard desktop & server releases, eg. Ubuntu 20.04 LTS, Ubuntu 20.10 being the 2020-April & 2020-October releases.

Ubuntu also has specialist (*snap* only) releases with a longer supported life, that use the *year* format, eg. Ubuntu Core 20 being the 2020 release (there is only a single release per even numbered year for these).

Do you mean Ubuntu Core 20?  intended for IoT appliance/devices? or cloud use?  

They are different products, and your Ubuntu 20 implies to me a *snap* only specialist release, but you likely mean a standard desktop release (*which will be 20.04 or 20.10 and not 20*)

---

### Post by anneranch on 2021-02-03
a@a-desktop:~$ uname -a
Linux a-desktop 5.8.0-41-generic #46~20.04.1-Ubuntu SMP Mon Jan 18 17:52:23 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by guiverc on 2021-02-04
You've provided kernel details, not Ubuntu release details.

Both Ubuntu Core 20, and Ubuntu 20.04 LTS can use the same kernel, in fact the 5.8 kernel is also used by Ubuntu 20.10, as 5.8 is the Linux kernel version, and not the Ubuntu release you're using.

There is no Ubuntu version 20.

You could mean 

- Ubuntu Core 20
- Ubuntu 20.04 LTS Server
- Ubuntu 20.04 LTS Desktop
- Ubuntu 20.10 Server
- Ubuntu 20.10 Desktop

as all currently can use the 5.8 kernel, though 20.04 LTS systems can also use the 5.4 kernel (*an option for Ubuntu 20.04 LTS Desktop, and 5.4 is the default kernel for Ubuntu 20.04 LTS Server*).

Bluetooth to me implies it's a desktop release you're using, so Ubuntu 20.04 LTS Desktop, or Ubuntu 20.10 Desktop; both of which use the 5.8 kernel (*20.04 having option to use 5.4 GA kernel if change*d).

---

### Post by deadflowr on 2021-02-04
Is there no settings option in the dropdown menu at the top right corner of the desktop?

---

