---
title: "About pdf file editing"
date: 2017-06-29
forum: General Help
---

### Post by satimis on 2017-06-29
Hi all,

I run PDFtK to extract certain pages on a PDF file;

```

$ pdftk original.pdf cat 1 output page-1.pdf

$ pdftk original.pdf cat 5 output page-5.pdf

$ pdftk original.pdf cat 12 output page-12.pdf

$ pdftk original.pdf cat 28 output page-28.pdf

```
etc

After adding notes on them how to merge them back to the original PDF file to replace/over-write their old pages?

Please advise.  Thanks in advice.

Regards
satimis

---

### Post by spjackson on 2017-06-29
I don't know how to replace individual pages, but if you extract **all **the pages, then make your changes, you can then cat them all back together,
```

pdftk cat page-1.pdf page-2.pdf... output original.pdf

```
If you extract them such that the names sort alphabetically into page number order you can then use a wildcard like:
```

pdftk cat page-*.pdf output original.pdf

```
Does this help?

---

### Post by satimis on 2017-06-29
> **spjackson said:**
> I don't know how to replace individual pages, but if you extract **all **the pages, then make your changes, you can then cat them all back together,
```

pdftk cat page-1.pdf page-2.pdf... output original.pdf

```
If you extract them such that the names sort alphabetically into page number order you can then use a wildcard like:
```

pdftk cat page-*.pdf output original.pdf

```
Does this help?
Hi,

Thanks for your advice.

I'm now doing it with following steps;

&#10219; pdftk original.pdf burst output output_%2d.pdf compress

&#10219; ls```

doc_data.txt
original.pdf
output_ 1.pdf
output_ 2.pdf
output_ 3.pdf
output_ 4.pdf
output_ 5.pdf
etc

```

Modified output_ 1.pdf and output_ 2.pdf

Run following command to re-combine;```

output_ 1.pdf
output_ 2.pdf
output_ 3.pdf
output_ 4.pdf
output_ 5.pdf
etc

```

&#10219; pdftk output_\ * cat output newfile.pdf

I'm now looking for a way adding back output_ 1.pdf and output_ 2.pdf, after modifying them, to the original PDF file without bursting all pages.

Regards
satimis

---

### Post by vanadium on 2017-07-01
Your current approach is good. You cannot directly insert a page in the middle with a single pdftk command. pdftk combines PDF's, but cannot replace in one step (afaik). Thus at the very least, you need two steps, one which splits the original PDF in two pieces, up to and not including the page you want to delete, and the remaining pages, and then a command merging both pieces and your updated page together.

---

### Post by satimis on 2017-07-01
> **vanadium said:**
> Your current approach is good. You cannot directly insert a page in the middle with a single pdftk command. pdftk combines PDF's, but cannot replace in one step (afaik). Thus at the very least, you need two steps, one which splits the original PDF in two pieces, up to and not including the page you want to delete, and the remaining pages, and then a command merging both pieces and your updated page together.
Hi,

Thanks for your advice.

I'm now running the steps mentioned on my previous posting to add signature and date on certain pages of a PDF file.  If the PDF file consisting >50 pages it will take some time to finish the job.

I'm searching around whether there will be a solution adding signature and date direct on PDF file without going through the mentioned steps.

Regards
satimis

---

