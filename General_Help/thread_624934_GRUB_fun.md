---
title: "GRUB fun"
date: 2007-11-27
forum: General Help
---

### Post by TV-VCR on 2007-11-27
Just curious, I've seen several photos and videos of the GRUB bootloader... having a true GUI? How do I get that? (on a non SuSE system)

Here's an example of what I mean: [http://www.youtube.com/watch?v=0szKrjzXMw0](http://www.youtube.com/watch?v=0szKrjzXMw0)

And also, how do you change the order of operating systems in the bootloader? I mean, I could Windows in front of Gentoo and vice versa.

Cheers. :)

---

### Post by mbeierl on 2007-11-27
That is GFXBOOT and it actually is an alternate package to grub.  Unfortunately it is not part of the standard Ubuntu install.

---

### Post by TV-VCR on 2007-11-27
> **mbeierl said:**
> That is GFXBOOT and it actually is an alternate package to grub.  Unfortunately it is not part of the standard Ubuntu install.

Can GFXboot be added to a GRUB install?

---

### Post by mbeierl on 2007-11-27
Haven't tried this in a while, but I did this long ago and it just worked:

[http://ubuntuforums.org/showthread.php?t=208855](http://ubuntuforums.org/showthread.php?t=208855)

---

### Post by mbeierl on 2007-11-27
Doh!  It seems as though it's already available in 7.10 (don't know about earlier) like so:
```

sudo aptitude install gfxboot gfxboot-theme-ubuntu

```

This page contains a recent summary of the howto:

[http://ubuntuforums.org/showthread.php?t=208855&page=48](http://ubuntuforums.org/showthread.php?t=208855&page=48)

And gfxboot does need grub-gfxboot debian package in order to work - it does need to be downloaded and installed from the link in the howto.

---

