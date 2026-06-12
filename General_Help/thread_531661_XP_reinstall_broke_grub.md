---
title: "XP reinstall broke grub"
date: 2007-08-21
forum: General Help
---

### Post by band-aid on 2007-08-21
Ok I'm sure you've heard this a million times before but the guides I have followed have not worked. Heres what I have done.

I rebooted my kubuntu live cd
opened up a root terminal
grub
grub> root ( <tab>
grub> root (hd0,1)
grub> setup (hd0) (I think)
grub> quit

Then I rebooted. Grub does come up and windows XP will boot but when I choose to boot ubuntu (or recovery) it gives me an error 17: cannot mount partition (or something similar). Any suggestions?

---

### Post by merlinus on 2007-08-21
```

sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

```Substitute results from find for (hdx,y).

-merlin

---

### Post by ronmarley1 on 2007-08-21
I posted this in response to your other question.  
You may want to try Super GRUB Disk.  It will search your hard drive and find GRUB (if it's there) for you and restore it.  Works great.  [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)
EDIT:  OOPS!  Sorry, I did not read your whole post above.  Maybe when you reinstalled XP it corrupted part of the Ubuntu install?  Sorry I'm not more help.

---

### Post by band-aid on 2007-08-22
find returned (hd0,1), and I went through the steps again and get Error 17: cannot mount selected partition. I think I may have messed something up when I was running through one of the guides. It had me mount /dev/sda2 (my root partition) and then run

grub-install --root-directory=/mnt/sda2 /dev/sda

So is find going to return the wrong directory?


EDIT: Ok I think its working. For some reason (probably my fault) grub didn't have the correct partitions in menu.lst for the various boot options. I switched it to the correct one and it boots. Thanks for the help.

---

### Post by merlinus on 2007-08-22
You might try supergrub, as ronmarley1 suggested.

Here is a link to more info:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

