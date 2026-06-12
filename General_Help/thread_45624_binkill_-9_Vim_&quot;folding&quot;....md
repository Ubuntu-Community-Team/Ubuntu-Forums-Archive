---
title: "/bin/kill -9 Vim &quot;folding&quot;..."
date: 2005-06-30
forum: General Help
---

### Post by skoal on 2005-06-30
How do I turn off, no, *destroy* vim "folding"?  I'm a long time Vim user and have never used (nor cared to use) this feature before.  Folding basically wraps (hides!) blocks of code like this (21 lines of latex code in the following example):

+-- 21 lines: Preamble:  \documentclass[12pt]{letter}---------------------------

* It's particularly annoying for someone like me who knows how to navigate around in Vim pretty fast, and prefers everything to be shown.

:note: a quick /<keyword> (search) in Vim apparently turns it off for that session.  I want to disable it permanently.

thx.

\\//_

---

### Post by skoal on 2005-06-30
Ooops! A reply unto myself! postcount++;

Anyways, I found various solutions to my problem.  Apparently the vim package is compiled in with +foldlevel support, which I've never used before, and which is quite frustrating for someone used to customization (especially while working with latex document settings).  There are various ways to work with them:

1. Go over the fold and hit 'zo' to *open* a fold.  Conversely, hit 'zc' to *close* a fold (if you still want to use them).

2. To turn them off completely (booyah!), set the "foldlevel" variable to a non-zero level.  ":set foldlevel=1" works.  Higher numbers affect it as well.  Without more poking around in vim docs than I care to, there is apparently a foldlevel limit, and it corresponds to said functionality, which I could give a ratt's rear end about.

\\//_

---

