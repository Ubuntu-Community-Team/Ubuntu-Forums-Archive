---
title: "Kernel compilation question"
date: 2013-01-20
forum: General Help
---

### Post by lonewolff on 2013-01-20
Hi Guys,
 
I was reading through the notes about **md** and it states
 
 **[FONT=Arial Narrow]When  md is compiled into the kernel (_not as module_), partitions of type 0xfd  are scanned and automatically assembled into RAID arrays.[/FONT]**
 
This leads me to my big question. How do you build RAID into the kernel and not as a module?
 
I can build the kernel from source with no problems but I do not know how to add things into the kernel.
 
Any guidance would by greatly appreciated [IMG]http://www.linuxforums.org/forum/images/smilies/icon_smile.gif[/IMG]

---

### Post by Doug S on 2013-01-20
the config file specifies if something is compiled into the kernel (y) or as a module (m)or not at all (commented out). Example, for MD related stuff (from an older build enviroment on my computer):```
doug@s15:~/temp-3.2.0.32/linux-3.2.0$ grep "CONFIG_MD" config
CONFIG_MD=y
CONFIG_MD_AUTODETECT=y
CONFIG_MD_LINEAR=m
CONFIG_MD_RAID0=m
CONFIG_MD_RAID1=m
CONFIG_MD_RAID10=m
CONFIG_MD_RAID456=m
CONFIG_MD_MULTIPATH=m
CONFIG_MD_FAULTY=m
```Often, the config file is auto generated from somewhere else. It has been a few months since I have built the kernel, so I forget some details.

---

