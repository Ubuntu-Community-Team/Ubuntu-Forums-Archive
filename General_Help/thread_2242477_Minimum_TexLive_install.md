---
title: "Minimum TexLive install??"
date: 2014-09-02
forum: General Help
---

### Post by ken18 on 2014-09-02
Is there such a thing as a minimum TexLive install?  If so, how is it done?

I just recently installed TexLIve using the TUG website and install-tl script.  The install took 1.5 hours and included so many packages I doubt I'll ever use.  What I want is a bare minimum install for pdflatex (with maybe 3 packages such as amsmath, color, pstricks) and then use tlmgr to install additional packages as I need them.

Appreciate advice / suggestions.  Thanks.

---

### Post by ken18 on 2014-09-03
After some digging I think I'm heading in the right direction.  When I first installed TexLive I used install-tl -gui=wizard instead of install-tl -gui=perltk.  Using install-tl -gui=perltk I can pick and choose the level of install.

---

