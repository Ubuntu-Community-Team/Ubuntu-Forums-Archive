---
title: "How to make Grub 2 as the default bootloader?"
date: 2008-06-22
forum: General Help
---

### Post by keplenk on 2008-06-22
Hi all,

I'm new to Linux and I'm hoping that somebody can help with my problem.

I've installed Grub2 in Synaptic and it went well.  However, when I restarted, I noticed that it was still using Grub Legacy and it just added an option "Chainload to Grub 2" in the menu.  When I highlight and press enter on it, it actually goes to Grub 2 (blue background screen).

Is there a way to make boot Grub 2 directly?  

What I did was set the timeout to 0 in menu.lst so that I will just go directly to Grub 2.  But I don't want that.  I want Grub Legacy to be gone permanently. Is there a way to just eliminate Grub Legacy?  What will happen if I delete menu.lst, will it just use grub.cfg?

Thank you.

Thanks

---

### Post by VMC on 2008-06-22
> **keplenk said:**
> Hi all,

I'm new to Linux and I'm hoping that somebody can help with my problem.

I've installed Grub2 in Synaptic and it went well.  However, when I restarted, I noticed that it was still using Grub Legacy and it just added an option "Chainload to Grub 2" in the menu.  When I highlight and press enter on it, it actually goes to Grub 2 (blue background screen).

Is there a way to make boot Grub 2 directly?  

What I did was set the timeout to 0 in menu.lst so that I will just go directly to Grub 2.  But I don't want that.  I want Grub Legacy to be gone permanently. Is there a way to just eliminate Grub Legacy?  What will happen if I delete menu.lst, will it just use grub.cfg?

Thank you.

Thanks

Here's some more info, but there is a warning that Grub2 doesn't understand NTFS:
[http://grub.enbug.org/TestingOnX86](http://grub.enbug.org/TestingOnX86)

---

