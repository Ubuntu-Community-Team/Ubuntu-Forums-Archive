---
title: "Where does Linux store optical drive parameters?"
date: 2007-01-17
forum: General Help
---

### Post by dwasifar on 2007-01-17
I think my system has a funny idea about the max CD writing speed of my DVD burner, because since upgrading to Edgy the available burn speeds in the Write to Disc window are mostly fractions - 14.1x, 18.8x, 28.2x, on up to 56.4x, which is past the drive's actual maximum speed.  

Where do I tell Ubuntu that the max CD write speed on this drive is 48x?

---

### Post by dwasifar on 2007-01-17
bumpity-bump

---

### Post by po0f on 2007-01-18
dwasifar,

Are you using nautilus-burn to write these CDs?  Try using [GnomeBaker](http://packages.ubuntu.com/edgy/gnome/gnomebaker); it has an option to detect the available write speeds of a drive.

---

### Post by dwasifar on 2007-01-18
> **po0f said:**
> dwasifar,

Are you using nautilus-burn to write these CDs?  Try using [GnomeBaker](http://packages.ubuntu.com/edgy/gnome/gnomebaker); it has an option to detect the available write speeds of a drive.
You know, I didn't even think of that, and I have GnomeBaker installed.  DUH!  I have gotten so used to just right-clicking an iso and choosing Write To Disc.  

Anyway, I tested GnomeBaker.  It reports the drive speeds correctly and works with no errors when copying a CD, but fails immediately when trying to burn an iso.  So I tried K3B, and that works fine with both.

I still wonder why nautilus burn is acting wonky, though.

---

