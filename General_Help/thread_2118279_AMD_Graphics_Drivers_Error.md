---
title: "AMD Graphics Drivers Error"
date: 2013-02-20
forum: General Help
---

### Post by BonceyDoesLinux on 2013-02-20
Need some help with this. I've searched for a few hours and found no answer that worked for me.

When I try to install my drivers I get

> One or more tools required for installation cannot be found on the system.
Install the required tools before installing the fglrx driver. Optionally, run the installer with --force option to install without the tools. Forcing install will disable AMD hardware accelleration and may make your system unstable.
Not recommended.
See /usr/share/ati/fglrx-install.log for more details.

So I checked that log and it gave me

> Supported adapter detected.
Check if system has the tools required for installation.
fglrx installation requires that the system have kernel headers.  /lib/modules/3.8.0-6-generic/build/include/linux/version.h cannot be found on this system.
One or more tools required for installation cannot be found on the system. Install the required tools before installing the fglrx driver.
Optionally, run the installer with --force option to install without the tools.
Forcing install will disable AMD hardware acceleration and may make your system unstable. Not recommended.

---

### Post by dcstar on 2013-02-21
> **BonceyDoesLinux said:**
> Need some help with this. I've searched for a few hours and found no answer that worked for me.

When I try to install my drivers I get



So I checked that log and it gave me

[LIST=1]
[*]Don't use "Quote" tags - they are for previous posts.
[*]```
Supported adapter detected.
Check if system has the tools required for installation.
[B]fglrx installation requires that the system have kernel headers.
/lib/modules/3.8.0-6-generic/build/include/linux/version.h cannot be found on this system.[/B]
One or more tools required for installation cannot be found on the system. Install the required tools before installing the fglrx driver. Optionally, run the installer with --force option to install without the tools. Forcing install will disable AMD hardware acceleration and may make your system unstable. Not recommended.
```
[/LIST]

---

### Post by Yellow Pasque on 2013-02-21
You need linux headers (and probably other packages). If you're trying to install fglrx/Catalyst manually, there's a guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

Actually, before you install fglrx, you should probably tell us what hardware you have, what Ubuntu you're running, and why the fglrx included with Ubuntu doesn't work. Lately, I've seen way too many incorrect assumptions from n00bs thinking they need to install a video driver (and they often screw up their systems that way).

---

