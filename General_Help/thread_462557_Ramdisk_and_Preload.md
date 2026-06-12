---
title: "Ramdisk and Preload"
date: 2007-06-02
forum: General Help
---

### Post by jabagawee on 2007-06-02
I've seen so many references to it, and I think it's a great idea. So how does one make a ramdisk? No matter how many posts about the thing, no one states outright how it's made.

On an unrelated topic, how does the preload package work? Does it anticipate what you're going to open, or does one need to configure it to tell it what to preload on boot. Can someone tell me this? :P

PS. Sorry if it's in the wrong forum. I don't know which forum to use.

---

### Post by revertex on 2007-07-12
preload do not preload on boot.

it analyze data, no need to configure.

i suggest you avoid it, since it don't bring any real benefit.

---

### Post by webjames on 2008-02-24
i beg to differ:

[http://www.techthrob.com/tech/preload.php](http://www.techthrob.com/tech/preload.php)

> sudo apt-get install preload

as simple as that.

---

### Post by revertex on 2008-02-24
well i express myself badly wrong, when i said " 		preload do not preload on boot", i mean preload do not preload the boot process, it loads itself on boot before user can login, that's why it loads desktop faster".

I still suggest avoid  preload, it may promises big improvements but seems buggy, troublesome old and abandonned.

The latest release is more than one year old.

If preload is wonderful as it says, why ubuntu don't use it as default?

---

