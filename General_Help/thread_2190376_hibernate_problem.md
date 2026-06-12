---
title: "hibernate problem"
date: 2013-11-27
forum: General Help
---

### Post by sedalatianz on 2013-11-27
Hey guys,
I'm having trouble enabling my hibernate feature.
I have installed Ubuntu 12.04 LTS 64bit using Wubi on my Asus N53SN hybrid laptop ( Intel + Nvidia). After Updating through ubuntu Update manager AND turning off my Nvidia card using Bumblebee, I no longer have an issue with suspending (aka standby, right?) my laptop and the laptop fan running at the full speed all the time. Oh and I also installed Jupiter and have set it on power saver ( CPU temp= 48 centigerades. is it ok?). any ways, I thought these were important to know in order for my problem to be solved.

So when I tried to hibernate using uswsusp, it seemed like ubuntu was doing some things, the colorful screen went black with white texts, it didn't turn off; but everything went back to normal (but there were no sound/wireless problem). having a 8gb ram, I checked my swap size and I thought that I should increase it. I did that using this code that is available on the WubiGuide:

```

[COLOR=#333333]sudo su
[/COLOR][COLOR=#333333]swapoff -a
[/COLOR][COLOR=#333333]cd /host/ubuntu/disks/
[/COLOR][COLOR=#333333]mv swap.disk swap.disk.bak
[/COLOR][COLOR=#333333]dd if=/dev/zero of=swap.disk bs=1024 count=2097152
[/COLOR][COLOR=#333333]mkswap swap.disk
[/COLOR][COLOR=#333333]swapon -a
[/COLOR][COLOR=#333333]free -m[/COLOR][COLOR=#333333]rm swap.disk.bak
[/COLOR]
```

(I thought 2gbs is ok since I won't have 2gb of applications running to take ram memory. maybe I am wrong here.)
then, I try :
```
 sudo s2disk 
```
but I get:
> s2disk: Could not use the resume device (try swapon -a). Reason: No such device

I do what he (!) asks, but nothing happens. I again try to run s2disk, but I get the same error.

can you help me out? I think since I have no trouble with with suspend then I am just one step away from having hibernate.

---

### Post by bcbc on 2013-11-27
Ubuntu uses a swap partition to hibernate. Wubi doesn't create partitions and uses a swap file instead.  So you cannot hibernate it.

It is possible to hibernate to a swap file, but I've never heard of anyone doing it on Wubi (I've seen some try). 

Note if you create a swap partition, you can hibernate a Wubi install, but most of the time people use Wubi to avoid repartitioning, so not really an option (in this case you might as well do a normal install).

---

### Post by acodea on 2013-11-27
> **sedalatianz said:**
> Hey guys,
I'm having trouble enabling my hibernate feature.
I have installed Ubuntu 12.04 LTS 64bit using Wubi on my Asus N53SN hybrid laptop ( Intel + Nvidia). After Updating through ubuntu Update manager AND turning off my Nvidia card using Bumblebee, I no longer have an issue with suspending (aka standby, right?) my laptop and the laptop fan running at the full speed all the time. Oh and I also installed Jupiter and have set it on power saver ( CPU temp= 48 centigerades. is it ok?). any ways, I thought these were important to know in order for my problem to be solved.

48C  is fine. I wouldn't worry until the sensors reach about 65C all the time, except blow away the fan dust now and then.


> ...can you help me out? I think since I have no trouble with with suspend then I am just one step away from having hibernate.

This is a feeling I get whenever I am tweaking Ubuntu. I am good, I think but Linux is a little better, an error may be just a design flaw.

---

