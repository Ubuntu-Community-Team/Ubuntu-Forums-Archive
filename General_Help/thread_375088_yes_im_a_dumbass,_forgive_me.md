---
title: "yes im a dumbass, forgive me"
date: 2007-03-03
forum: General Help
---

### Post by quiksliver on 2007-03-03
Hi there

I install ubuntu yesterday and partitioned a drive into three parts, so i could dual boot, I didn't care for it but thats besides the point

this morning instead of doing the smart thing and uninstalling, i went into windows and using paragon partition editor i just deleted the three partitions

now whenever i try to boot it gives me a "GRUB loading... GRUB error 22"

is there anyway to boot into windows or is reformatting my only option? I don't see why because all i need to do is "override" this command and boot into windows...

---

### Post by Irony on 2007-03-03
Not sure what you mean - just reinstall ubuntu to one of the free partitions.

Or you can fixmbr with your windows disc.

The grub error just means that grub can't find your grub menu in ubuntu because you've deleted it.

---

### Post by m.musashi on 2007-03-03
Grub is looking at a no longer existing partition for the menu and such to start. To fix it so you can boot windows you need to replace your MBR. I can't remember the steps and usually end up looking it up but I think you boot using the XP CD and use the recovery consol. From there you run fixmbr. I think I usually ran fixboot too. I'll dig around and see if I can find the right steps but that's the general idea. In any case, you don't need to reformat.

---

### Post by Joshua on 2007-03-03
Do you have a windows recovery disk?  I think if you can get to the console with that and do:
```
fdisk /mbr
```
you should get a normal boot into windows from that point on.

This is the method recomended by the [GRUB FAQ]("http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q12"), but I think the fixmbr thing works as well.

---

### Post by m.musashi on 2007-03-03
Okay, check [url=http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true
]this MS site[/url] for some info.

You might also want to check [here](http://users.bigpond.net.au/hermanzone/p6.htm) for some general info on MBR and Ubuntu. This is a good site for various things related to dual booting.

---

