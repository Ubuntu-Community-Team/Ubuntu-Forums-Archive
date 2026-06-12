---
title: "How do I add support for the Reiser4 fs on Ubuntu 6.06?"
date: 2006-09-29
forum: General Help
---

### Post by solarwind on 2006-09-29
Hi all,

How do I add support for the Reiser4 fs on Ubuntu 6.06? I am using a laptop that I need to travel with a lot. I have heard that Reiser4 fs is the best fs for laptops because of minimal disk writes. (Or is it the best fs for a laptop? If not, then what fs is best for a laptop that travels a lot?). I need support for the Reiser4 fs on my Ubuntu 6.06. How do I do this?

---

### Post by croak77 on 2006-09-29
You'll need to patch the kernel or use pre-patched kernel sources. I would just stick to ext3 for now.

---

### Post by solarwind on 2006-09-30
Thanks, but I really need the reiser4 fs. If I patch the kernel sources, when I re make the kernel, will the entire kernel need to be built again, or just the module or everything all over again?

Thanks very much in advance.

---

### Post by croak77 on 2006-09-30
> **solarwind said:**
> Thanks, but I really need the reiser4 fs. If I patch the kernel sources, when I re make the kernel, will the entire kernel need to be built again, or just the module or everything all over again?

Thanks very much in advance.

You can use reiser4 but it's most likely not the best filesystem for a laptop, ext3 is. I've never added resier4 support to Ubuntu so I have no idea what has to be done or how stable the result will be.

---

### Post by graigsmith on 2006-09-30
that depends, is reiser 4 the most stable file system? one that can handle direct power outages?  it is a laptop after all.

---

### Post by solarwind on 2006-09-30
> **graigsmith said:**
> that depends, is reiser 4 the most stable file system? one that can handle direct power outages?  it is a laptop after all.

Yes, it is. I like the fs. How do I add support for it?

---

### Post by croak77 on 2006-10-01
> **solarwind said:**
> Yes, it is. I like the fs. How do I add support for it?

Just so you know, Reiser4 is not the most stable fs. For help take a look at this;
[http://www.namesys.com/install_v4.html](http://www.namesys.com/install_v4.html)

You also might need to patch grub to work with reiser4. I'm not sure if the Ubuntu grub package is already patched. But ext3 with dir_index is what I would recommend. If you want, you can use reiserfs (reiser3) for a /usr or /var partition. Reiserfs is great with small files.

---

### Post by PriceChild on 2006-10-01
I really think you should research more on this file system, your answers so far appear as though you have just heard one person raving about it and treated it as gospel.

There is a reason the ext3 is used by default in ubuntu. Its primarily down to stability. At the end of the day, minimal disk writes doesn't mean too much, it won't be much less but also reducing stability.

If i were you i would do a LOT more research before committing a large amount of time and effort towards what may be a fruitless goal.

---

