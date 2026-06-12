---
title: "Formating changed in OpenOffice documents after upgrade from Dapper to Feisty"
date: 2008-05-03
forum: General Help
---

### Post by Seb71 on 2008-05-03
I upgraded one of my computers from Ubuntu 6.06 to Ubuntu 7.04 (clean install).

Since then I have some problems with some OpenOffice.org templates (.ott) and documents (.odt) made using those templates.
[B]
For the same OpenOffice.org text document or template, the formatting changes depending on the Ubuntu version I use.[/B]

The templates contain some text with Gentium (Bold) font inside a table (a fax header page).

The width of the cell was adjusted for the minimum value that still keeps the text in one row (one line) inside the cell.

Since upgrading from Ubuntu 6.06 to Ubuntu 7.04 (also, I've tried 7.10 and 8.04 with same results like in 7.04), the text no longer fits inside the cell. Now, some rows have the text inside split on two lines.

In order that the same text (with the same Gentium bold) fits inside the table cell on one line (on one row), I have to either decrease the font size from 10 to 9, or to enlarge the table cell width.

I have tried the same templates in OpenOffice (2.4 and 2.3) for Windows (were I also have the Gentium font installed) and they are displayed correctly (like in Ubuntu 6.06). So this seems to exclude a OppenOffice.org bug.

In all OS-es, the Gentium font seems to be the same: version 1.02/2005.

---

### Post by Seb71 on 2008-05-04
**You can replicate this bug as follows** (if you have Windows XP or Ubuntu 6.06 and Ubuntu 7.04, 7.10 or 8.04):
- Create a text .odt document in OO.org (2.3 or 2.4) from Windows (or from Ubuntu 6.06).
- Make a table.
- Write some text inside a cell table.
- Change the font of the text to Gentium Size 10 and apply Bold to it.
- Adjust the colum width to the minimum width that still keeps the text inside the cell on one line.
- Save the document.
- Open the document with OpenOffice.org from Ubuntu 7.04 or from Ubuntu 7.10 or from Ubuntu 8.04.
- The text inside the table cell will now be split on two lines (it no longer fits inside the same width of the column).

With Times New Roman font this does not seem to happen.

You can download Gentium font from [here]("http://scripts.sil.org/cms/scripts/page.php?site_id=nrsi&item_id=Gentium").

What might be the problem? The Gentium font? Ubuntu? OpenOffice.org?

---

