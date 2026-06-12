---
title: "FLTK dev: segfault when rendering text?"
date: 2005-05-24
forum: General Help
---

### Post by josh2112 on 2005-05-24
Has anybody else run into FreeType problems doing FLTK development on Hoary?

Whenever I try to custom-draw some text (for example in my own Fl_Browser_ subclass) using fl_draw() I get a segfault.  The crash occurs inside fl_font_xft.cxx.  FLTK uses libxft1, I believe, for font rendering.

I built FLTK from source and had the same problem, so it's not Ubuntu's packaging of FLTK that's at fault.  All my packages are up-to-date as of this morning.  fl_draw works fine with libxft1 and FLTK 1.1.6 (built from source) on my Redhat 7.2 and Fedora Core 3 boxes.

Is this some issue with Ubuntu's libxft1?

Thanks,
  Josh

---

### Post by josh2112 on 2005-05-25
Err... ignore all that.  It was a mistake in my code... had to set the font before calling fl_draw().  Sometimes the most complex problems have the simplest solutions...

---

