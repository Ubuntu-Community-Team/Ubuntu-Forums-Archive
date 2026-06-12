---
title: "Do not load, always being sent to command :("
date: 2007-02-27
forum: General Help
---

### Post by teft on 2007-02-27
hi

this is my problem:
I installed the ext2 driver to share files between windows and ubuntu, also, I have ntfs-3g in ubuntu, so I decided to uninstall ext2 driver...I've restarted my pc and tried to load ubuntu but I just do not complete the load bar, in fact I loads only 10% of the bar, then I go to command interface and this error came up

```
/bin/sh: can't acces tty; job control turned off
```

can I fix it with any command? I tried looking in the list of aviable commands but I dunno what to do

thanks

---

### Post by jron on 2007-02-27
I can confirm a variant of this bug in both 6.10 and herd 4. Upon booting from the desktop cd, I can see a few PCI errors, then the ubuntu screen shows up with the progress bar. then, I am kicked out to the BusyBox prompt with the error: can't access tty; job control turned off. 

My laptop is an hp dv4030us (almost 2 years old)

when I remove the splash from loading, I see these last 4 lines before the BusyBox prompt:
[     4.080000] hda: cache flushes supported
[     4.080000] hda: hda1 hda2
[     4.096000] hdb: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, DMA
[     4.096000] Uniform CD-ROM driver Revision 3.20

BusyBox v1.1.3....

When I allow the splash and hit alt+f1 to view the PCI errors I see:

[      31.114234] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0 
[      31.114286] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[      31.114234] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
Loading, please wait...

typing "can't access tty; job control turned off" into google brings up TONS of the same questions.

Here are some of the better posts on the issue:
[http://paste.ubuntu-nl.org/7886/](http://paste.ubuntu-nl.org/7886/)
[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57502](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57502)

in the first post, it is interesting in that the author claims this issue does not exist in FC4 and another distro.

It looks as if this bug has been around for almost a year? what gives? is there any solution for me other than shelling out for an external cdrom drive? that seems a tad ridiculous to me =(

also, teft, you may want to change the title of this post to something like: boot failure: can't access tty; job control turned off

---

### Post by teft on 2007-02-27
and you mean this is an issue using the live cd? It used to work good in the hard drive until I made that change... with the driver in windows, I tried booting from an older version of the kernel but always the same thing, Im really new with ubuntu so I dunno what to do, in the first post recommend to upgrade the BIOS but, mine is up to date... anything else? thanks

---

### Post by jron on 2007-02-28
yeah, I tried updating my bios too; no luck. I hear about this error mostly from the desktop cd trying to load, but i've also heard of many cases like yours.

---

