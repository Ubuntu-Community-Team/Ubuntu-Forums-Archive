---
title: "libre office vs ms office"
date: 2013-01-11
forum: General Help
---

### Post by i argor on 2013-01-11
hello,

i currently have major trouble with my office documents which are made with libreoffice. 

when i create a document in libreoffice everything is fine, even after converting into doc type format the display of that document within libreoffice is fine. but when some one else opens it with fkn ms office its all screwed up

how can i make sure that my documents look the same in ms office, what is about rtf file type?

i don't use any ms products anymore and i don't want to buy ms windows nor office just because of ms word is not able to display the document properly.

regards 

Mark

---

### Post by mike555 on 2013-01-11
If the documents don't need to be edited send out .pdf  , that way the document will look exactly like you made.

---

### Post by Hagar Delest on 2013-01-24
That's the vendor lock-in policy! And that's why it's important to use true open formats like ODF.

The MS Office import/export filters have been reverse engineered, they have not been made to be compatible with anything else than MS Office. Same with OOXML (.docx, ...) BTW.

PDF is the best bet indeed if the file has not to be edited.

---

### Post by Warren Hill on 2013-01-24
The MS office import and export is less than perfect.  Partly because of differences in standard fonts between Windows and Linux.  Given that Microsoft 
have never released documentation for the file format it actually does a very good attempt.

If you need to allow people to edit your word files its worth spending some time deciding which fonts and font sizes transfer the best.  If not send people a pdf as suggested by others in this thread,

---

### Post by prodigy_ on 2013-01-24
> **i argor said:**
> what is about rtf file type?

RTF should work - it's a portable format. Although I'm not sure it can preserve all the formatting that you can have in ODF or DOC/DOCX. But it's worth a try anyway.

> **Warren Hill said:**
> Given that Microsoft 
have never released documentation for the file format it actually does a very good attempt.
Yes they did. You can d/l the specification [here](http://download.microsoft.com/download/0/B/E/0BE8BDD7-E5E8-422A-ABFD-4342ED7AD886/Word97-2007BinaryFileFormat(doc)Specification.pdf).

---

### Post by Hagar Delest on 2013-01-24
But I'm not sure that the specification covers all areas of the file formats. I remember some discussions about proprietary features referenced in the spec and not documented at all.

---

### Post by kurt18947 on 2013-01-24
Regrettably, if you need 100% compatibility, you need MS Office for reasons cited above.  File lock-in is worth $many millions to MS and they're not going to surrender that advantage willingly.  Could you get an inexpensive copy of home & student MS Office and install it using something like playonlinux or crossover office?  Reportedly older versions of MS Office work quite well using one of those to install.  MS Office went to the xml file formats starting with Office 2007 so I guess 2007 or newer should work as well as MS Office works between versions.  If you are a student or know one, there are academic discounts available.  New MS Office versions are supposed to support .odf.  It'll be interesting to see how well and if it can export or just import.

---

### Post by bodhi.zazen on 2013-01-24
> **i argor said:**
> hello,

i currently have major trouble with my office documents which are made with libreoffice. 

when i create a document in libreoffice everything is fine, even after converting into doc type format the display of that document within libreoffice is fine. but when some one else opens it with fkn ms office its all screwed up

how can i make sure that my documents look the same in ms office, what is about rtf file type?

i don't use any ms products anymore and i don't want to buy ms windows nor office just because of ms word is not able to display the document properly.

regards 

Mark

It depends on what you use the documents for. 

The solution I would offer is to tell your friends/family to install libre-office.

It is free and works on windows.

[http://www.libreoffice.org/](http://www.libreoffice.org/)

---

### Post by Warren Hill on 2013-01-24
> **prodigy_ said:**
> RTF should work - it's a portable format. Although I'm not sure it can preserve all the formatting that you can have in ODF or DOC/DOCX. But it's worth a try anyway.


Yes they did. You can d/l the specification [here]("http://download.microsoft.com/download/0/B/E/0BE8BDD7-E5E8-422A-ABFD-4342ED7AD886/Word97-2007BinaryFileFormat(doc)Specification.pdf").

I stand corrected.  Thanks for the info

---

### Post by Calinou on 2013-01-24
> **bodhi.zazen said:**
> It depends on what you use the documents for. 

The solution I would offer is to tell your friends/family to install libre-office.

It is free and works on windows.

[http://www.libreoffice.org/](http://www.libreoffice.org/)

Seconded -- it'd be quicker for most people who want to read your document to download LibreOffice instead of whining about you not making your documents in .doc(x) format. :p

---

### Post by Mark Phelps on 2013-01-25
> **i argor said:**
> ... how can i make sure that my documents look the same in ms office,  If the other folks are using MS Office 2007 or newer, the default filetype for saving documents is "docx" -- which Non-Windows products have a hard time using.

> what is about rtf file type? It is "rich text" which allows you to save the text of the format, but it is not an exact conversion and some features are likely to be lost.

> i don't use any ms products anymore and i don't want to buy ms windows nor office just because of ms word is not able to display the document properly.

It's not displaying it that is the problem -- the problem is that when folks save the document, it automatically converts it into a format that YOUR document app can not handle. If they're presented with the option of either (1) saving the documents in .doc format or learning a whole new way to do what they are already doing in MS Word by having the install and learn LibreOffice -- it's likely they would choose the first.

---

### Post by SeijiSensei on 2013-01-25
You can save directly from Open/LibreOffice in older MS formats like .doc and .xls.  You can even configure those programs to use the MS formats as the defaults rather than the ODF formats.  Still you'll find they will not transfer perfectly unless the documents are fairly simple ones.

Here's an example of how problems arise.  MS uses the printer driver when formatting a document to ensure it looks as good as possible on the chosen printer.  Open/LibreOffice obviously cannot do that since CUPS doesn't use the MS drivers.

As for the proprietary formats, there are some aspects of the DOCX specification that include instructions like "Format Like Word97".  The specification may be open, but some of the directives rely on proprietary features of MS Office.

---

