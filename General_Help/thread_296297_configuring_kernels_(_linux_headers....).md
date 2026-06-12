---
title: "configuring kernels??? ( linux headers....)"
date: 2006-11-09
forum: General Help
---

### Post by Ryupower on 2006-11-09
Hi, I'm trying to configure a graphic tablet kernel ( Wacom Graphire ).
I put :
 sudo dpkg-reconfigure wacom-kernel-source

OK, so it starts, I go on "OK" "YES"....

And then it wants to know the location of my linux headers!
I take the default, says it is not a valid location,
then I enter:
 /usr/src/kernel-headers-2.6.11.2

doesn't work.

I tried different ones but non of them are valid!
I went to look at that directory ( /usr/src/ )
and nothing was there that said something like "Kernel" I only had 'modules' and something 'rpm'.
I go on modules and it has a directory called "wacom", but I don't think the kernel is configured.

Anyways, ignoring that, my problem is:
[B]Nothing in that directory has anything about kernels.
And I have no valid kernel entry.[/B]

I typed kernel in the search, and I found a kernel-headers.deb package.
I clicked on it but it said it was already installed.
I'm kinda n00b-ish, so tell me what's up please. :)

---

### Post by nikhilk on 2006-11-09
Maybe you need to install the appropriate linux-headers package.

---

### Post by Ryupower on 2006-11-09
> **nikhilk said:**
> Maybe you need to install the appropriate linux-headers package.

I have one package which came with my ubuntu install.
I thought that would be the right one.

---

