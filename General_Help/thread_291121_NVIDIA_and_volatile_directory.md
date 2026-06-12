---
title: "NVIDIA and volatile directory"
date: 2006-11-02
forum: General Help
---

### Post by masticazzi on 2006-11-02
Hi all,

yesterday I was playing with NVIDIA beta drivers.

I used NVIDIA's installer which works *almost* like a charm.. except that the *charm* ends after a reboot.

In fact, when I reboot, modprobe loads an old module instead of the proper one, causing X not to start.

I have removed the old kernel modules and done a "depmod"... and works... but.. suddenly, alter a reboot, those modules are back there!!!

the directories involved are:

/lib/modules/kernel_version/volatile  (where modules *appears*)
/lib/modules/kernel_version/kernel/drivers/video (where my latest module is)

and 

/lib/linux-restricted-modules/kernel/

Can anybody tell me how comes modules are recreated in the volatile directory? Can you please point me to the right documentation?

What's linux-restricted-modules for?

Thanks
Alessandro

---

### Post by DomQ on 2007-04-24
[INDENT]*Can anybody tell me how comes modules are recreated in the volatile directory?*
[/INDENT]

It's a trick from [FONT="Fixedsys"]/sbin/lrm-manager[/FONT], a Debian-only script that takes care of relinking binary-only kernel modules so that their usefulness survives a kernel upgrade. This mechanism provides some amount of support for binary-only kernel modules, which is necessary since the mainline kernel [expresses the attitude]("http://www.linuxjournal.com/article/6152") of not supporting same.

I couldn't find any documentation to speak of, but [FONT="Fixedsys"]/sbin/lrm-manager[/FONT] is only 87 lines long in Feisty. Good luck!

---

