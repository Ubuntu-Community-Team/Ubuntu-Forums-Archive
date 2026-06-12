---
title: "Booting an ISO from GRUB"
date: 2007-01-24
forum: General Help
---

### Post by musther on 2007-01-24
I often find myself wanting to test a live CD, such as Feisty Fawn herd 2, and don't like burning a CD every time.  Sometimes I use vmware, but if I want to get the authentic experience (for whatever reason), then I need to boot it somehow.

I've been wondering if it's possible to boot an ISO on the hard disk directly from GRUB, I looked around and apparently it's quite easy, by adding this to your menu.list:

```
title Boot from iso on a harddisk
map (hdX,Y)/your.iso (hdZ)
map --rehook
chainloader (hdZ)+1
rootnoverify (hdZ)
boot
```

The place I found that also said 'The iso file must be in one chunk - contig from sysinternal'.

Firstly, does anybody know if this is the correct way to do if (if it can be done), and if so how do I make sure the ISO is 'in one chunk'?

Thanks

---

### Post by mmcmonster on 2007-01-27
If you manage to get this to work, can you please post your example?  I'll try to google for more info, but nothing's come up yet. :-(

---

### Post by musther on 2007-01-27
Haven't got it to work.  I can see what the above is trying to do, but I don't thing Grub's map command can do that?  I couldn't find any more info.

---

