---
title: "unable to update!"
date: 2007-09-20
forum: General Help
---

### Post by el_ricardo on 2007-09-20
hello all, i've just decided to go back to ubuntu, after having a lot of trouble with gentoo, I've just installed the ubuntu ultimate edition, and now i've got round to updating the system. The updater has got as far as "xserver-xorg-core", and something's gone wrong! I went into synaptics, and chose "fix broken packages" and this did something, as now xserver-xorg-core is the only marked update, and is highlighted yellow in synaptics. When i try to install it, i'm given the following error message:

```

dpkg: error processing /var/cache/apt/archives/xserver-xorg-core_2%3a1.2.0-3ubuntu8_i386.deb (--unpack):
 trying to overwrite `/usr/share/man/man1/scanpci.1.gz', which is also in package gatos
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/xserver-xorg-core_2%3a1.2.0-3ubuntu8_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

does anyone have any ideas? i've googled around, but i found no specific references to this problem!

thanks in advance for any responses!

---

### Post by el_ricardo on 2007-09-20
problem solved! I found [this]("http://ubuntuforums.org/archive/index.php/t-425568.html") from googling just part of the error message, said this problem was fixed in an update, but obviousy not entirely because i just enountered it!

---

### Post by aonegodman on 2008-01-10
Well I've got a similar problem so let me hop on your post so I might pull an answer from someone. Thanks!

E: /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.4_i386.deb: trying to overwrite `/usr/lib/libmjpegutils-1.8.so.0.0.0', which is also in package libmjpegtools0c2a

That's the current error I get when trying to fix broken packages in Pkg Mngr.

?

---

