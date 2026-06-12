---
title: "Kernel Compiliation problems (2.6.13)"
date: 2005-09-06
forum: General Help
---

### Post by duminas on 2005-09-06
OK, why is this so bloody difficult?
I tried following **both** of the howto documents available on the forums in regard to doing this. The first time it broke halfway through the compile. This time, it compiled and built fine (as well as the nvidia module .deb), but now it kernel panics about being unable to sync the root VFS or something of that sort.

Are boot logs stored anywhere when the kernel panics?
I hate trying to scribe these errors down, since they're often much too verbose for me to remember. ;_;

And I think I did remove VFS support somewhere, but I can't find it again in *xconfig* (it was a filesystem, if memory serves), so I'm not sure where to check. Also... why exactly should VFS be freaking out? My partitions are either ext3 or reiser, which I built directly into the kernel.

Sorry if this is confusing, and thanks for any help.
If you need any more information, by all means ask and I'll try to find it.

[size=1]Basically, I just removed SCSI and Firewire, as well as a lot of drivers for USB devices I don't use.[/size]

---

### Post by nszabolcs on 2005-09-06
[QUOTE=duminas]
Are boot logs stored anywhere when the kernel panics?
[/QUOTE]
try
/var/log/syslog
or
/var/log/kern.log

---

