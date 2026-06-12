---
title: "rxvt-unicode bold fixed font problems"
date: 2008-03-03
forum: General Help
---

### Post by ewaters on 2008-03-03
I've been using aterm for years now.  I'd like to switch to rxvt-unicode (urxvt) due to it's much better memory usage (20 MB for aterm vs. 4MB for urxvt).  The biggest hurdle is that I really like small consoles (8pt).  I use the 'fixed' font:

  .font: -*-fixed-medium-r-normal--8-*-*-*-*-*-*-*

Aterm creates a bold version that looks great.  urxvt (and any other console I've tried) will not:

  [IMG]http://demeter.uarc.com/~ewaters/aterm_vs_urxvt.png[/IMG]

Is there anything to be done?  Aside from turning off bold text, I'd like to find a way to keep my attractive looking fixed ( size 8 ) font and also have the extra info conveyed by bold fonts.  I've tried lots of other fonts and can't find another that works.  I've also tried using:

[INDENT]URxvt.boldFont: -*-fixed-medium-r-semicondensed--8-*-*-*-*-*-*-*
URxvt.boldFont: -*-fixed-bold-r-normal--8-*-*-*-*-*-*-*
URxvt.boldFont: -*-fixed-bold-r-normal--*-*-*-*-*-*-*-*
URxvt.boldFont: -*-fixed-bold-*-*--*-*-*-*-*-*-*-*[/INDENT]

but none of them look any better.

Edit: Using gbdfed, I was able to create my own bold varient that looks exactly the way I like (just like aterm rendered it).  I offer it here for anyone else who needs it:

  [http://demeter.uarc.com/~ewaters/fixed-5x8-bold.pcf.gz](http://demeter.uarc.com/~ewaters/fixed-5x8-bold.pcf.gz)

Provides:

  -misc-fixed-bold-r-normal--8-80-75-75-c-50-iso10646-1

Eric Waters

---

