---
title: "How to print two A5 pdf pages on a single A4 sheet?"
date: 2007-08-27
forum: General Help
---

### Post by Arjunanda on 2007-08-27
I have several A5 sized documents that I would need to print on a single A4 sheet. In evince I can print several pages on one sheet. Nice. But it does not make any use of the page size. Two A5 sheets fit perfectly on A4 without any zooming, but evince zooms them down by 50% of the original size leaving much empty space on the sheet and making the text too small.

Is there any practical way I could do this, other than 1) buying A5 paper, 2) printing one A5 page per one A4 sheet, 3) re-formatting the pages into A4 and then printing with evince two pages on one sheet. All these mentioned methods are not the optimal solution I am looking for.

---

### Post by cwaldbieser on 2007-08-27
> **Arjunanda said:**
> I have several A5 sized documents that I would need to print on a single A4 sheet. In evince I can print several pages on one sheet. Nice. But it does not make any use of the page size. Two A5 sheets fit perfectly on A4 without any zooming, but evince zooms them down by 50% of the original size leaving much empty space on the sheet and making the text too small.

Is there any practical way I could do this, other than 1) buying A5 paper, 2) printing one A5 page per one A4 sheet, 3) re-formatting the pages into A4 and then printing with evince two pages on one sheet. All these mentioned methods are not the optimal solution I am looking for.

If you are comfortable using command line tools, you could try using the "ps*" tools from the gs-common package.  E.g. pdf2ps, psmerge, ps2pdf, etc.

---

