---
title: "smbmount and utf-8 characters"
date: 2007-01-04
forum: General Help
---

### Post by Markus72 on 2007-01-04
Hi,

I'm running a samba 3.0.20 server on a NSLU2 ([http://www.nslu2-linux.org/](http://www.nslu2-linux.org/)) and it worked (and works) fine from the beginning.

I configured the unix character set in samba to UTF-8 and both Windows and my Ubuntu client can access the shares without a problem.

Even the German umlauts are displayed perfectly - as long as I do not mount the shares using mount (smbmnt).

Then the German umlauts are corrupted. That means: using that network-server browsing functionality in edgy (gnome) I have a very slow connection but all characters look as they have to.

If I mount that same share, the filenames with umlauts are pure garbage.

I tried to mount with all possible iocharset and codepage parameters but none did the trick.

What's the thing I've forgotten? Is it possible at all? Do I have to use cifs instead (I don't want to)?

Any idea?

Thanks
Markus

---

