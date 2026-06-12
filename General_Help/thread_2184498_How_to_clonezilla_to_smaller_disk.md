---
title: "How to clonezilla to smaller disk ??"
date: 2013-10-29
forum: General Help
---

### Post by forums2 on 2013-10-29
Hi All,

I'm trying to clone a Kubuntu installation from a 250gb disk to a 120Gb SSD but I'm unable to.

I've restore installation to another 250Gb disk and shrink main  partition to only 50gb, but when I try to clone to the 120Gb SSD  Clonezilla still says destination disk is too small.

Then I've try to clone partition (not disk) but clonezilla returns a weird error, something like "Box partition doesn't exist".

Can someone tell me how to archieve this succesfully? A link to a how-to or something like this.

Many thanks in advance

---

### Post by sudodus on 2013-10-29
Clonezilla works in such a way, that it can clone to the same size or larger drives.

But if you make your image of the installed system with ***tar***, you can expand it to a smaller drive (but obviously it must be big enough for all the files and the file system journal). This is what I do with the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971"). Another alternative is ***fsarchiver***.

---

