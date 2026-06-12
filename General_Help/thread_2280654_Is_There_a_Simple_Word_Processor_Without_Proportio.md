---
title: "Is There a Simple Word Processor Without Proportional Spacing?"
date: 2015-06-01
forum: General Help
---

### Post by oldefoxx on 2015-06-01
Or can I turn off Proportional Spacing In LibreOffice Writer?  I'm trying to write or import simple table structures written with a text editur, and the columns become a zig-zaggedy in word processors because of proportional spacing.

Or is there a text editor that allows multiple fonts, bold, italics, and underscoring?  I'm trying to find an in-between solution here. I could actually do without the multiple fonts, but it doesn't hurt to ask.

---

### Post by coffeecat on 2015-06-01
If you don't want to use the table feature of LibreOffice, you should be able to do what you want by using a monospace font. Have a search through the available fonts in the font drop-down list. Anything with "mono" in the name should be mono-spaced.

---

### Post by sudodus on 2015-06-01
You can select a mono-space font for the tables in LibreOffice's word processor, for example Courier, Courier New or Ubuntu Mono. That should do trick for you. You mark part of the document and select font for the marked part.

Or you can treat the tables in LibreOffice's spreadsheet processor and import the tables to the word processor.

---

### Post by oldefoxx on 2015-06-03
Thanks for the suggestions.  I haven't tried using tables in LibreOffice, but I will look into it.  Trouble with importing contents from a spreadsheet is you don't get just the displayed data, you get the cells themselves.  What I do get the contents alone is to select a cell and press in sequence the F2, F9, Enter, Enter.  This replaces the formula in that cell with the data displayed there. Somebody told me this pn a different thread. 

I can't find answers as to what it does or how it works.  One bad thing is you lose the real contents for good in the cells you do this to, and you might trying to just copy and paste that cells to another spreadsheet (or place in this spreadsheet) so that you can use the steps given to do a replacement there.  But the cloned cells may react badly in terms of relative addresses used within.  And you still copy the cell structure over when you paste into Writer.  I end up

Picking cell9s0 to bring over to Writer
First get those cell(s)' ontents to appwar in a second range of cells  (you can do this with '=' and first cell address in the second group of cells).Highlight the range of second cells and do F2, F9, Enter, Enter
Copy these second cells into your Writer document.  Pase below the point where you are writing.  You get all the cells with the displayed data in each.
Copy each cells contents to the place where you want it in your document.
Delete the cells (table) that you inserted.

Or just leave the table intact after you paste it into your document.  If somebody knows a better method, I would be glad to be so advised.

Playing with LibreOffice Calc, under data it allows you to select an XML Source file, but everything else is grayed-out.  As to doing conversions, your only Export formats are html, xhtml, and pdf.  But under the Save As... "" Format options you find CSV as a choice.  Now if you could just  somehow get an html, xml, xhtml, or csv file ti load properly into Cal, that would be something.  But I can't find or figure out how.

---

### Post by Vaphell on 2015-06-03
wouldn't ctrl+c in calc, ctrl+shift+v (paste special...) in writer work? It offers the option to paste plain text and i am not getting any table cells nor formulas here.

---

### Post by HermanAB on 2015-06-03
It can be very trying to import data into a wordconfuser such as Soffice.  What I do in such a case, is to copy and paste the data into a text editor like Gedit, fix it up the way I want it, then copy and paste it from gedit into the wordconfuser, then set the font to Courier New.

---

