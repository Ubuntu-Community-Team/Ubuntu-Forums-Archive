---
title: "locale settings + latex template = messed up characters"
date: 2008-02-07
forum: General Help
---

### Post by kung fu buntu on 2008-02-07
Things were working fine when I was using CMU's latex template for my thesis.
But my university decided to provide a template for all dissertations.

The problem is that now, non-ascii characters get messed up.
For example, instead of "Stéphane Laveau" I get "StÃl&#8217;phane Laveau" or " StÃ©phane Laveau" (last on if I use inputenc package).
Going update all the names in the bib file isn't an option, because there are a lot of them and I don't have the time.

I tried to compare both templates in order to identify the problem, but I had no success even though I set equal the "items" I found suspicions.
In the .cls file I have:```

...
\DeclareOption{en}{%
  \let\@language=1%
  \PassOptionsToPackage{english}{babel}}
...
\ExecuteOptions{en,twoside,premei,print}
\ProcessOptions
....
....
\RequirePackage[latin1]{inputenc}

```
One thing I don't understand is how that code is translated to "\usepackage[english]{babel}"

I have a bad feeling that this may be some locale colisions....
On my linux system I use LANG=en_US.UTF-8 and use a portuguese keyboard.

---

### Post by kung fu buntu on 2008-02-08
fixed with a "\RequirePackage[utf8]{inputenc}" in the .cls file

---

