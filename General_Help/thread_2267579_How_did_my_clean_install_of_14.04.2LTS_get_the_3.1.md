---
title: "How did my clean install of 14.04.2LTS get the 3.16 kernel?"
date: 2015-03-02
forum: General Help
---

### Post by justen_m on 2015-03-02
How did my clean install of 14.04.2LTS get the 3.16 kernel? I think the title says it all. WTF? My other box has been upgraded regularly, even with dist-upgrades, and are still at 13.13 kernel. How did my initial install of 14.04.2 give me the 3.16 kernel? Did I miss that in the installation instructions?

Damn it, I am on 14.04LTS because I want all four of my systems the same. Easier to support. Now I've got a freakin' new kernel on one. When I boot... This is the ONLY kernel that shows up.

---

### Post by gifford on 2015-03-02
Because 14.04.2 uses the 3.16 kernel. 14.04 and 14.04.1 uses the 13.3 kernel and will not update to the 13.16 kernel unless you do the LTS Hardware Enablement Stack.
See this link: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by grahammechanical on 2015-03-02
> [COLOR=#333333][FONT=Ubuntu Beta]In an effort to support a wider variety of hardware on an existing LTS release, the 14.04.2 point release will ship with an updated kernel and X stack by default. This newer hardware enablement stack will be comprised of the kernel and X stack from the Utopic 14.10 release.[/FONT][/COLOR]

> [COLOR=#333333][FONT=Ubuntu Beta]By default, the 14.04.2 point release will ship with a newer [/FONT][/COLOR][3.16]("https://launchpad.net/ubuntu/+source/linux-lts-utopic")[COLOR=#333333][FONT=Ubuntu Beta] Linux kernel from Ubuntu 14.10, and a matching X.org stack. This is based on the [/FONT][/COLOR][3.16.0]("http://kernel.ubuntu.com/git?p=ubuntu/linux.git")[COLOR=#333333][FONT=Ubuntu Beta][/FONT][/COLOR][Extended Upstream Stable Kernel Release]("https://wiki.ubuntu.com/Kernel/Dev/ExtendedStable")[COLOR=#333333][FONT=Ubuntu Beta]. The purpose of providing a newer kernel in the 14.04.2 point release is for hardware enablement. [/FONT][/COLOR]

[https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes/](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes/)

If it was up to you Ubuntu 14.04 would not be compatible with hardware released after April 2014.

---

### Post by justen_m on 2015-03-14
Ah, thanks grahammechanical. The other systems, which have been upgraded from various initial installs, report being 14.04.2 but the kernel wasn't upgraded, while my clean 14.04.2 install was. So I upgraded the rest manually as described on the link you provided. Thanks again.

---

