---
title: "My Wubi Suggestions"
date: 2007-10-06
forum: General Help
---

### Post by natoodo on 2007-10-06
I have a few suggestions for future vesions of wubi :):):)


These may be far fetched, mayby a little bit crazy, but it may give you developers an idea on what wubi could be like. 

My suggestions are,

1.Allow for more than one linux distribution ex. fedora core, open suse, ect.

2. Allow for a possible duel boot or maybe allow for as many wubi installed versions of linux as the user has hdd space for. 

3. Make wubi a insalled program that can add/remove different linux installations as the user wills, and to resize the virtual disks.

4. Allow for custom virtual disk sizes.

5. May maybe include lvpm and a free partition manager to install linux to unallocated space.

These are a few of my suggestions. If you have any please feel free to share more or if mine are a bit dumb or stupid :confused: also feel free to share.

By for now:)

---

### Post by SpiritIsReality on 2007-10-06
howdy
so wubi is kinda like a virtual machine?
[http://www.pcworld.com/article/id,137631-c,software/article.html](http://www.pcworld.com/article/id,137631-c,software/article.html)
buds

---

### Post by ago on 2007-10-06
> **fmat said:**
> howdy
so wubi is kinda like a virtual machine?
[http://www.pcworld.com/article/id,137631-c,software/article.html](http://www.pcworld.com/article/id,137631-c,software/article.html)
buds

Nope wubi is more like a real installation, the main difference from a real installation is that it does not require a dedicated partition.

---

### Post by ago on 2007-10-06
> **natoodo said:**
> 
1.Allow for more than one linux distribution ex. fedora core, open suse, ect.
There is unetbootin  for that [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html) written by Geza, one of wubi devs. For loopinstallations (installation without partitioning) though each distribution needs to change a few things internally. We do not have the resources to do that ourselves.

> 2. Allow for a possible duel boot or maybe allow for as many wubi installed versions of linux as the user has hdd space for. 
It is better to have just ubuntu and install different desktop environments IMO. Also there is a trade-off between features and simplicity. And I tend to favour the second aspect. More advanced users are encouraged to install ubuntu properly and use grub.

> 3. Make wubi a insalled program that can add/remove different linux installations as the user wills, and to resize the virtual disks.
Some of that can be done by wubi, [http://lubi.sourceforge.net/](http://lubi.sourceforge.net/)

> 4. Allow for custom virtual disk sizes.
Do you mean resizable virtual disks? That may happen in next version.

> 5. May maybe include lvpm and a free partition manager to install linux to unallocated space.
The plan is to merge lvpm with ubiquity (official ubuntu installer) so that it would be possible to migrate existing wubi installations to a dedicated partition.

---

### Post by SpiritIsReality on 2007-10-06
howdy
ago ...thankyou

buds

---

