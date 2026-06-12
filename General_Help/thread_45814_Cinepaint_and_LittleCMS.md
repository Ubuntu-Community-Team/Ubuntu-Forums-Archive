---
title: "Cinepaint and LittleCMS"
date: 2005-07-01
forum: General Help
---

### Post by nwillis on 2005-07-01
Hiyo.  Has anybody gotten Cinepaint to work with LittleCMS support?  I know I have lcms installed and set up correctly; it works flawlessly with Scribus.  But nogo on Cinepaint.

What gives?

Thanks,
N

---

### Post by nwillis on 2005-07-02
Well, since no one else seems to care, I'll just post what I learn here for my own amusement and to warn future readers with this same concern:

It appears that color-managment is not built in (or rather not default) until Cinepaint 0.19.  So until Ubuntu upgrades to 0.19 (which was Jan '05) your only option is compiling it yourself.

If you do so, be forewarned that there are a lot of dependencies and the "configure" supplied in the official download does a bad job of checking for them.  It took me a while to track down compiler errors that usually boiled down to an #include directive failing because of some unlisted dependancy (e.g., PNG and TIFF development packages).

So pretty much install every image/graphics related package with "-dev" on its name before you begin.

Happy Hunting.
Nate

---

