---
title: "ATI driver Patch, Ubuntu/Gentoo compatibility"
date: 2007-01-09
forum: General Help
---

### Post by constanthatz on 2007-01-09
I am new Ubuntu/Linux user trying to get the s-video to function on my ATI video card in my IBM T42.  Forgive me if this is a stupid question.

After following various how-tos I was led to this Gentoo patch,[ http://bugs.gentoo.org/show_bug.cgi?id=127642]("http://bugs.gentoo.org/show_bug.cgi?id=127642"), for the xf86-video-ati-6.6.2 driver source, which I got here [http://xorg.freedesktop.org/releases/individual/driver/xf86-video-ati-6.6.2.tar.gz]("http://xorg.freedesktop.org/releases/individual/driver/xf86-video-ati-6.6.2.tar.gz").

I downloaded the driver source, extracted the files, copied the patch file into the extracted folder, and ran this command:

patch <patch_file.patch

I got a bunch of hunk failed and can't find files to patch errors, even though those files existed and if my understanding of the -p argument for the patch command is correct, it should have found them alright.

My question is, was this failed from the start?  Can this patch be applied directly to the driver source using the patch command, or is it written in such a way that it can only be used with Gentoo/portage/ebuild.

Thanks.

Edited for spelling, clarity.

---

