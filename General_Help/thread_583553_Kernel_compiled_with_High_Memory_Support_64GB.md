---
title: "Kernel compiled with High Memory Support 64GB ?"
date: 2007-10-20
forum: General Help
---

### Post by lauris on 2007-10-20
Hi,

 Is there a place I could download deb file of  2.6.22-14-generic kernel compiled with High Memory Support 64GB ? 

I`m running into issues while trying to do it myself (my compiled kernel gets 2.6.22.9 version, while I expect it to be 2.6.22-14, nvidia drivers failes to load with the new kernel and so on).

Thanks for help.

---

### Post by Rikiji on 2007-10-22
same problem here.

---

### Post by PmDematagoda on 2007-10-22
So why don't you use Ubuntu 64 bit?

---

### Post by lauris on 2007-10-22
Because the only 64 bit "thing" I need is support for 4GB of ram and 32bit kernel is perfectly capable to do that.

I spend few hours trying to compile new one, following [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) and common sense, but the new one gets version 2.6.22.9 (why, oh why?), which means recompilation of linux-restricted-modules (which failes) to get the right version of nvidia kernel module.

If someone has right version of files and could spend a little time making deb of 2.6.22-14-generic with High Memory Support 64GB it would be great.

---

### Post by Rikiji on 2007-10-22
> **PmDematagoda said:**
> So why don't you use Ubuntu 64 bit?

My laptop can't run the live 64 bit version, and also installing via alternate gives me many problems with xserver.
I had to work through command line to reinstall nvidia drivers, and then it says me it is impossible to install them because my kernel 2.6.22.9 isn't supported. dunno. :confused:

A precompiled version of the kernel with the only difference in 64 GB support would be great.

---

