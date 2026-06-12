---
title: "How to change pdf font color"
date: 2017-06-19
forum: General Help
---

### Post by satimis on 2017-06-19
Hi all,

Following command works seamlessly changing pdf background/page color;

```

$ convert mydoc.pdf -background "#ffd9cf" -flatten mydoc_pink.pdf

```

Can I run convert to change pdf font color?  If YES please advise HOW?

Thanks

Regards
satimis

---

### Post by HermanAB on 2017-06-19
Yes, you should be able to change black to red or whatever with Imagemagick.  It has a fuzzy colour indicator that works something like this:

convert image -fuzz XX% -fill red -opaque white result where -fuzz XX% allows the match to white to get colors within XX% of white.

Read the man page or search for howtos - I'm not an Imagemagick expert and only use it once every few years.

---

### Post by satimis on 2017-06-20
Hi all,

Following commands work for me changing the font colour on the .pdf file;

1)
Command:
&#10219; convert -density 300 mydoc.pdf -alpha copy -background red -flatten mydoc_red.pdf

2)
Command:
&#10219; convert -density 300 mydoc.pdf -alpha copy -background '#1cb7fb' -flatten mydoc_blue.pdf

Thanks

satimis

---

