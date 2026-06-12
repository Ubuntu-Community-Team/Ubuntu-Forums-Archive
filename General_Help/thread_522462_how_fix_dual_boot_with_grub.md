---
title: "how fix dual boot with grub ?"
date: 2007-08-10
forum: General Help
---

### Post by afrb on 2007-08-10
I downloaded Ubuntu Feisty Fawn, and installed it on my laptop, above Windows XP. Everything works just fine. My question is whether I can get some kind of "grub" to rebuild the boot stuff quickly, if I need to. I believe that the last act of the installation process was to create the boot sector and/or boot records, but re-installing Ubuntu is an inconvenient way of doing this again later.

When I turn on the computer I get a window that offers five possibilities:
1.Ubuntu Linux
2.ditto "restore"
3.some other flavor of Ubuntu
4.Windows XP
5.Windows XP Restore (the XP that came with the laptop has a D-disk primary partition that the user isn't supposed to mess with, which will be a great resource if a restore is necessary. This partition apparently was seen by the Ubuntu installer, and caused this to be included in the boot menu.)

Numbers 1 and 4 work perfectly; 2 and 3 I haven't tried; number 5 I early tried out of curiosity, and I'm afraid of hitting it again by accident. I don't know quite what it's supposed to do, but the first thing it does is to mess up the boot mechanism.

I have a Partition Commander CD that offers all kinds of tools, and one of them is to rebuild the boot sector. So I tried that. It worked very quickly, and then I was able to boot Windows XP. But it didn't seem to do anything for booting Linux.

So I just re-installed Ubuntu, and all is well again.

But there must be some way I can boot from a CD, and find on the CD a "grub" that will look at the hard disk the way the last act of the Ubuntu installer did, and create something that gives me the choice of booting Linux or Windows. Can you tell me what to do?

---

### Post by merlinus on 2007-08-10
SuperGrub:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Detailed info about its use:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

