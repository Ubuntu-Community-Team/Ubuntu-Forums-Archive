---
title: "PDF Arranger in UbuntuStudio 20.04.1 destroys internal links"
date: 2020-09-01
forum: General Help
---

### Post by Nosphky on 2020-09-01
Using 18.04 in mid-July, I merged a cover.pdf with a body.pdf using pdf shuffler and the resulting output.pdf was fine. The body.pdf contains a contents page with internal links to each chapter. It also contains some external links. The cover.pdf document is only a single page. After merging with pdf shuffler, all links, internal and external, continued to work fine.

At the end of July, I made a fresh install upgrade to UbuntuStudio 20.04.1. which came equipped with PDF Arranger.  I expanded the body.pdf by a few pages and used PDF Arranger to merge it with cover.pdf. In the output file, none of the internal links worked after the merge. The external links were ok.  In fact, simply opening the body.pdf file in PDF Arranger and exporting it under a different name without any merging is sufficient to destroy the internal links.

I tried to find pdf shuffler but it seems that PDF Arranger is its successor. 

 I solved my immediate problem by installing a snap package of pdftk - its output file had all internal links working. I would prefer the gui application to the command line one because it's easier to rearrange pages if needed.

Does anyone have a suggestion for persuading PDF Arranger to merge two files without destroying the internal links?

---

