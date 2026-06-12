---
title: "Product information from Windows disk mounted in Ubuntu?"
date: 2017-11-29
forum: General Help
---

### Post by tommy2k10 on 2017-11-29
I work with computers and have taken a disk out of a machine that had a Blue Screen of Death, put it in my Linux system and mounted it.
Because I cannot access Windows (due to thousands of bad sectors) I cannot get the product codes from the software installed on the disk.
I backed the data up using MiniXP (as the Ubuntu Live CD wouldn't mount the disk for some reason).
On my own Windows system I use BelArc Advisor to get my system specs, which include software and hardware listings and product codes.
Is there some alternative software for Linux that can do the same things (software listing and product codes) and if so, can I point it to the Windows disk? (that is, if thhe data can be read!)

---

### Post by dragonfly41 on 2017-11-29
[COLOR=#000000]*"the Ubuntu Live CD wouldn't mount the disk for some reason"*

[/COLOR]If this is a problematic Windows NTFS disk you can try mounting it in Ubuntu by first installing ntfsfix in Ubuntu.

[http://manpages.ubuntu.com/manpages/xenial/man8/ntfsfix.8.html](http://manpages.ubuntu.com/manpages/xenial/man8/ntfsfix.8.html)

then in Ubuntu run ... sudo ntfsfix /dev/sdx

where sdx is the partition number.

---

### Post by tommy2k10 on 2017-11-29
> **dragonfly41 said:**
> [COLOR=#000000]*"the Ubuntu Live CD wouldn't mount the disk for some reason"*

[/COLOR]If this is a problematic Windows NTFS disk you can try mounting it in Ubuntu by first installing ntfsfix in Ubuntu.

[http://manpages.ubuntu.com/manpages/xenial/man8/ntfsfix.8.html](http://manpages.ubuntu.com/manpages/xenial/man8/ntfsfix.8.html)

then in Ubuntu run ... sudo ntfsfix /dev/sdx

where sdx is the partition number.

I will try that when I boot using the Live CD

For some reason, it mounts on my system  where Linux is actually installed, but not in a system where I use the  Live CD! (don't know why)

---

### Post by tommy2k10 on 2017-11-29
I still need to know please:

Is there some alternative software for Linux that can show product codes and software listings, and if so, can I point it to the Windows disk?

---

### Post by dragonfly41 on 2017-11-29
I don't know for sure and I have Windows+Ubuntu dual boot.  
But this article which I found explains how to use Live USB to extract the C:/windows/System32/config data and process it in another Windows environment.

[https://www.howtogeek.com/64600/how-to-recover-windows-and-software-keys-from-a-broken-computer/](https://www.howtogeek.com/64600/how-to-recover-windows-and-software-keys-from-a-broken-computer/)

and here ...

[https://www.howtogeek.com/206329/how-to-find-your-lost-windows-or-office-product-keys/](https://www.howtogeek.com/206329/how-to-find-your-lost-windows-or-office-product-keys/)


[Later edit]

Actually found some ideas here ... in this forum ..

[https://ubuntuforums.org/showthread.php?t=1249597](https://ubuntuforums.org/showthread.php?t=1249597)

---

### Post by tommy2k10 on 2017-11-29
> **dragonfly41 said:**
> I don't know for sure and I have Windows+Ubuntu dual boot.  
But this article which I found explains how to use Live USB to extract the C:/windows/System32/config data and process it in another Windows environment.

[https://www.howtogeek.com/64600/how-to-recover-windows-and-software-keys-from-a-broken-computer/](https://www.howtogeek.com/64600/how-to-recover-windows-and-software-keys-from-a-broken-computer/)

and here ...

[https://www.howtogeek.com/206329/how-to-find-your-lost-windows-or-office-product-keys/](https://www.howtogeek.com/206329/how-to-find-your-lost-windows-or-office-product-keys/)


[Later edit]

Actually found some ideas here ... in this forum ..

[https://ubuntuforums.org/showthread.php?t=1249597](https://ubuntuforums.org/showthread.php?t=1249597)

Thankyou, I will have a look at that.

---

