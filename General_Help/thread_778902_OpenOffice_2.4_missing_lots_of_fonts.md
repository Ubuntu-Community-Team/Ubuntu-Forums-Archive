---
title: "OpenOffice 2.4 missing lots of fonts"
date: 2008-05-02
forum: General Help
---

### Post by Codename46 on 2008-05-02
Hey,

I just recently upgraded 7.10 to 8.04. Upon opening Openoffice 2.4, I noticed that the default font is Nimbus Roman No9 L and popular fonts such as Times New Roman and Arial are missing.

I was wondering if there was any way to restore these fonts. I have an essay to write, and it would suck if the TA who receives my submission would have problems reading it if he doesn't have the same font I'm using.

Thanks.

---

### Post by billgoldberg on 2008-05-02
Open a terminal and copy/paste this:

sudo apt-get install msttcorefonts

That will install these fonts:

    * Andale Mono
    * Arial Black
    * Arial (Bold, Italic, Bold Italic)
    * Comic Sans MS (Bold)
    * Courier New (Bold, Italic, Bold Italic)
    * Georgia (Bold, Italic, Bold Italic)
    * Impact
    * Times New Roman (Bold, Italic, Bold Italic)
    * Trebuchet (Bold, Italic, Bold Italic)
    * Verdana (Bold, Italic, Bold Italic)
    * Webdings

---

