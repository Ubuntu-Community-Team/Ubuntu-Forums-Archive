---
title: "two AbiWord questions"
date: 2008-01-11
forum: General Help
---

### Post by DouglasAWh on 2008-01-11
1. So, I was thinking that the PDFs AbiWord created it would be able to open back up, but this does not appear to be the case.  My hour-glass replacement wheel thingy just spins and spins.  Should I be able to open said PDF?

2. Why does AbiWord not do *.odt?  Is there some sort of extension I can install to do *.odt?

Thanks!

---

### Post by strabes on 2008-01-11
You need to use evince to open/read pdf files.  When you double click on a .pdf it should open with evince by default. Abiword *does* do .odt files. I just installed it, opened a .odt file, edited it, and saved it.

---

### Post by DouglasAWh on 2008-01-12
When I try to save a document in AbiWord, it absolutely does not give odt as an option.  How to I make it show up?  

I just tried to open an odt and it gives PK????????[&#152;7^Æ2 instead of the actual text.  If I open it up in OOo 2.3, I get an 11 page document.  I am using AbiWord 2.4.6.

I can read PDF files just fine, but it seems silly that I can edit a PDF after saving as and keeping the document open, but I can't open that same PDF in AbiWord.

Additionally, is there a way to make OOo give .abw as an option?

---

### Post by DouglasAWh on 2008-01-13
Just saw on the AbiWord Wikipedia entry the confirmation odt.  So....why does mine not?

EDIT: so, I decided to uninstall and reinstall, using aptitude.  Now it works properly on the odt part.  Yay!  Still doesn't appear to read PDFs it created, but that's ok.  Now the question is, how do I make *.odt the default format.

EDIT 2: I found [http://www.abisource.com/mailinglists/abiword-user/2006/Jun/0046.html](http://www.abisource.com/mailinglists/abiword-user/2006/Jun/0046.html) for the default odt issue, but it didn't initially seem to work.  There are two <scheme> tags.  Make sure to use the one that has name = "custom"

---

