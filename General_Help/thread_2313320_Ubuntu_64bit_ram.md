---
title: "Ubuntu 64bit ram"
date: 2016-02-11
forum: General Help
---

### Post by Edward 000 on 2016-02-11
So I was using Ubuntu 32bit because my new Graphics card drivers couldn't handle 64bit bit so today I updated my Bios and the installed 64bit without any problems but the only problem I have is that it's showing less RAM (I have 4 gigs) on 32bit It showed 3.9 GB  but now on 64bit it's showing that I have 3.4GB. On Windows it shows that I have 4GB Installed so the problem is with Ubuntu I think. Thanks

---

### Post by newbie-user on 2016-02-11
Do you have an integrated graphics card? Those will borrow memory from RAM. Also, check the units. Ubuntu may be reporting in gibibytes instead of gigabytes.

---

### Post by Edward 000 on 2016-02-11
> **newbie-user said:**
> Do you have an integrated graphics card? Those will borrow memory from RAM. Also, check the units. Ubuntu may be reporting in gibibytes instead of gigabytes.

Thanks for the reply. No the Graphics card is not Integrated (Nvidia GT610) . I am Using Ubuntu 15.10 :)

---

### Post by newbie-user on 2016-02-12
Ubuntu reports memory that is available for use after the computer boots. That's probably why you're seeing 3.4GB. For example, I've got 16GB in my system and it's only reporting 15.1GB. Some memory is used for graphics, some used for the kernel, or whatever else needs to use ram. So Ubuntu looks at what's left and reports that.

---

