---
title: "Patch for THC Hydra (from Arch Linux User Repositories)"
date: 2008-06-05
forum: General Help
---

### Post by violagirl23 on 2008-06-05
I'm not an Ubuntu user but my friend is and he told me everyone has issues with THC Hydra, and when I told him it was in the unofficial repos for my distro (Arch Linux) and I just had to type yaourt -S hydra and it compiled and installed perfectly with no errors, he didn't believe me. Turns out that the version in the Arch user repositories (AUR for short) has a patch for configure called configure.patch.
Here is the URL for hydra in the AUR:
[http://aur.archlinux.org/packages.php?ID=4458](http://aur.archlinux.org/packages.php?ID=4458)
Here is the link to the patch:
[http://aur.archlinux.org/packages/hydra/hydra/configure.patch](http://aur.archlinux.org/packages/hydra/hydra/configure.patch)

According to the PKGBUILD (the thing that builds the package for you automatically), you have to do
```
patch -p0 < ../configure.patch > /dev/null
```
to apply the patch. Then you can just do ./configure, make, and then make install like normal.
It works on 64 bit really well.

So I hope that this might help someone. I love Arch Linux so much. :D No offense, but there's no way I'd want to use Ubuntu with something like Arch around. But I thought I'd spread this patch since no one outside of the Arch community seems to know about it.

---

### Post by abzman2000 on 2008-06-09
this makes it so simple (I couldn't do it before), it was very nice to put this out here, I certainly have never heard of this, what about anyone else?

---

### Post by K.Mandla on 2008-06-10
Moved to General Help.

---

