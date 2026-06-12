---
title: "Apt is recommanding x86_64 packages on i386"
date: 2008-06-24
forum: General Help
---

### Post by SpookyET on 2008-06-24
I don't understand why apt is showing me x86_64 kernel packages. It wants to upgrade my kernel to x86_64. 

[IMG]http://www.studioindustryllc.com/user/spookyet/miscellaneous/apt_x86_64_on_i386.png[/IMG]

---

### Post by drs305 on 2008-06-24
If you look closely, it says "x86/x86_64" which covers both systems. Synaptic/apt knows what system your computer is using and will display the correct packages for that architecture.

---

### Post by avtolle on 2008-06-24
Apt is not trying to install the 64 bit kernel. Rather, as to the header package you highlighted, the package is for either the 32 bit or the 64 bit kernel (the use of the slash likely is confusing).

---

### Post by SpookyET on 2008-06-24
> **drs305 said:**
> If you look closely, it says "x86/x86_64" which covers both systems. Synaptic/apt knows what system your computer is using and will display the correct packages for that architecture.

Oh, I missed that. I thought it's x86_64 only because .19 won't boot. .16 boots.

---

### Post by drs305 on 2008-06-24
> **SpookyET said:**
> Oh, I missed that. I thought it's x86_64 only because .19 won't boot. .16 boots.
If you are sure you are running 16 (you can check with "uname -r") you can uninstall the 19 kernel of linux-image and then reinstall **linux-image**.
You don't need to specify a kernel number as this will install the latest and all the dependencies.

---

