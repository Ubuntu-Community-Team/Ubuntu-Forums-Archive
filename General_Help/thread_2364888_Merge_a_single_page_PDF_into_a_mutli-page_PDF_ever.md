---
title: "Merge a single page PDF into a mutli-page PDF every other page"
date: 2017-06-29
forum: General Help
---

### Post by abonsey on 2017-06-29
I'm trying to merge a static single page PDF into a newly created multi-page PDF being placed every other page.
I've used to merge mutli-page with multipage:

pdftk A=odd_pages.pdf B=even_pages.pdf shuffle A B output collated_pages.pdf


What I'm after is A to be a single page PDF.

Anybody know who to do this PDFtk??

Thanks for any help

---

### Post by HermanAB on 2017-06-29
Prolly easier to do it with pdfshuffler.

---

### Post by vanadium on 2017-07-01
With some scripting. With pdftk, burst the PDF in single pages, e.g.
```

pdftk multipage.pdf burst temp%04d.pdf

```
Then use bash to create the single page for each of the pages of your multi-page PDF, something like
```

for f in  temp*.pdf
do cp single.pdf $(basename "$f" pdf)-2.pdf
done

```

Then combine all test*.pdf files back into one new multi-page PDF.

---

