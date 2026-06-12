---
title: "Photoshop 7.0"
date: 2007-07-02
forum: General Help
---

### Post by Baelfael on 2007-07-02
I installed Photoshop 7 using WINE and the only thing I am having problems with is text.

When I try to type using the text tool, it says I can't because a default system font could not be obtained.

Anyone know how to fix this?

---

### Post by dboot on 2007-07-10
Wine doesn't come with some fonts that windows applications need. You have to find out which font you need for Photoshop 7.0, download it, and put it in ~/.wine/drive_c/windows/fonts directory.

Try out [Wine-doors]("http://www.wine-doors.org/wordpress/?page_id=3"). It comes with several fonts that are commonly needed.

Good Luck!

---

### Post by bobshowrocks on 2007-07-10
Or if your dual booting with a windows version, you could jump in there quickly install photoshop, jump back into ubuntu and copy over the fonts to the correct spot in wine.

---

