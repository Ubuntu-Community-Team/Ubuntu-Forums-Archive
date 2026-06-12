---
title: "USB with Fake CDFS partition"
date: 2015-02-04
forum: General Help
---

### Post by rizwan7 on 2015-02-04
[COLOR=#333333][FONT=UbuntuRegular][B]Screenshot:

[/B][/FONT][/COLOR]
[CENTER][COLOR=#333333][FONT=UbuntuRegular][B][IMG]http://i.stack.imgur.com/jhoPB.png[/IMG]
[/B][/FONT][/COLOR][/CENTER]
[COLOR=#333333][FONT=UbuntuRegular]**What happened:**[/FONT][/COLOR]

[LIST]
[*]I installed Ubuntu 11.10 on USB in USB disk.
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]**The Problem:**[/FONT][/COLOR]

[LIST]
[*]I can not remove this CD drive partition, even after partition, it's still there. While boot from USB, it shows 'boot from CD-ROM' in boot menu.
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]**I tried:**[/FONT][/COLOR]

[LIST]
[*]I tried partition with a number of tools, including Windows partition, kill drive and Rufus. But nothing worked at all. At the end of every experiment, all I have is removable disk(remaining partition) is formatted but no effect on CDFS partition.
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]**Why it sucks?**[/FONT][/COLOR]

[LIST]
[*]I have lost almost 700MB of my USB disk. But this is not the issue, the real issue is that this USB disk does not boot with any other operating system. I tried to make a bootable Windows USB disk but all it does is only boot this silly CDFS partition with Ubuntu 11.10 setup.
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]**Additional Details:**[/FONT][/COLOR]

[LIST]
[*]This is an 8GB USB flash disk. Divided into 2 partitions, 1-Removable & 2-CD.
[/LIST]

---

### Post by sudodus on 2015-02-04
Welcome to the Ubuntu Forums :-)

Have you got any computer that is running linux? I mean without booting from this very pendrive (because you should boot from another drive than the one you want to change).

In that case we can try some linux tools to wipe the partition table and create a new one. I don't know Windows well enough to do those tasks (but I'm sure there are tools in Windows that can do it too).

---

