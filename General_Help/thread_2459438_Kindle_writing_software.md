---
title: "Kindle writing software"
date: 2021-03-18
forum: General Help
---

### Post by Philip_Edwards on 2021-03-18
Hi,
I'm looking for some software to help me write in Kindle e-book format.
I found a reference to a piece called Alkinea on these forums, but I don't know whether the pages are still active. Last reference that I could find was dated 2013.

I did manage to download the software but it doesn't want to install.
I could try to install it from Terminal, if I only knew how.

Yours,
Phil

---

### Post by dragonfly41 on 2021-03-18
Depending on content you might need a toolchain.
There are several paths to explore:
(a) Write in Calibre then export to Scribus (for printing colours). Search "kindle" in Scribus forum.
(b) Write in Atom editor (in markdown) and preview/publish through markdown-preview-enhanced package.
(c) Explore pandoc for document conversion.

---

### Post by ActionParsnip on 2021-03-18
Doesn't it read PDF? Could use Libreoffice and print to PDF

---

### Post by DuckHook on 2021-03-18
> **dragonfly41 said:**
> …Explore pandoc for document conversion.
Had not known about pandoc. Thanks for the heads-up. Do you find that, on doc conversions, so much formatting gets jumbled that it's not really usable/worth the effort?
> **ActionParsnip said:**
> Doesn't it read PDF? Could use Libreoffice and print to PDF
As e-books, I find PDFs to be sub&#8209;optimal. They are designed to display statically, usually as US Letter or Euro A4, whereas the advantage of e-books is displaying dynamically and auto&#8209;reformatting to fit screens of any size.

---

### Post by ActionParsnip on 2021-03-18
> **DuckHook said:**
> Had not known about pandoc. Thanks for the heads-up. Do you find that, on doc conversions, so much formatting gets jumbled that it's not really usable/worth the effort?

As e-books, I find PDFs to be sub&#8209;optimal. They are designed to display statically, usually as US Letter or Euro A4, whereas the advantage of e-books is displaying dynamically and auto&#8209;reformatting to fit screens of any size.

I see, well, it's an option I guess.

---

### Post by grahammechanical on 2021-03-18
LibreOffice Writer has options to Export as EPUB and Export directly as EPUB. It is found under File>Export As. I have not tried it yet. So, I cannot confirm its usefulness.

Regards

---

### Post by Holger_Gehrke on 2021-03-18
[Alkinea]("http://soft.alkinea.net/download.html") is just a converter for turning a OpenOffice / Libreoffice document into an epub file. If you have Amazons kindlegen installed, Alkinea can use that to generate a file in the old Kindle format (mobi) file from the epub. Problem with that is that kindlegen is discontinued since August of last year and is no longer available from Amazon and that there is a new format for the Kindle (azw3) ...

The general ebook suite Calibre includes an editor that can handle both epub and the newer Kindle format. If you need to generate files in the old format you can create your book in the newer format and use the converter in Calibre to produce a mobi file.

Holger

---

### Post by Impavidus on 2021-03-18
I haven't got a kindle, but have a kobo e-reader.  I write most (practically all) of my stuff in LaTeX, then I use make to turn that into pdf, ps or epub. For pdf or ps, make first creates a dvi, then converts it to pdf or ps. For dvi, make runs latex and the indexing tools as often as required. Page dimensions can be set to A4, A5 or the dimensions of my e-reader. For epub, make pipes the tex file through some sed scripts to remove the complex macros and replace them by something simple, then uses pandoc to generate the epub. I lose some quality that way, but pandoc can't handle the more complex stuff (and neither can epub format or my e-reader, I think).

On the e-reader, both pdf and epub have some advantages. In epub I can use chapters (should be possible in pdf too, but haven't figured that out yet), mark words, add comments and look up words in a dictionary. In pdf I get better typesetting (proper whitespace, flawless hyphenation, smallcaps, all kinds of TeX specialities) and math expressions work. Some of these may work in epub on other e-readers, but not on mine.

---

### Post by ajgreeny on 2021-03-18
I have some experience of using calibre very successfully but this is one of the very few occasions when it is worth getting the application direct from the developers, [https://calibre-ebook.com/download_linux](https://calibre-ebook.com/download_linux) which has version 5.13, rather than the repos which have 4.99.
It is possible to convert many filetypes such as .doc, .odt, even .txt to .mobi files very easily and quickly, though I have never done this with anything containing images or graphics so if that is important to you I am not sure how well it will work for you.

However, are you aware that it is possible to simply send a variety of documents to a kindle account by email where they are then converted into a kindle readable format.
I have never actually done this but if you did not know this was possible have a look at:-
[https://www.amazon.com/gp/sendtokindle/email](https://www.amazon.com/gp/sendtokindle/email)
[https://www.amazon.com/gp/help/customer/display.html?nodeId=G5WYD9SAF7PGXRNA](https://www.amazon.com/gp/help/customer/display.html?nodeId=G5WYD9SAF7PGXRNA)

This may not be what you're looking for as I presume a document sent by email will be limited to that Amazon/kindle account only and not transportable to other Amazon/kindle accounts, though I may have that wrong.

---

