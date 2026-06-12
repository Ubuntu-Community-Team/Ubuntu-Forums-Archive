---
title: "Embedded open fonts in portable documents"
date: 2018-01-25
forum: General Help
---

### Post by VanillaMozilla on 2018-01-25
I just got a shock.  I've been distributing PDF files for years, secure in the knowledge that the viewer would see and print exactly what I had written.  But when I printed one of my own documents on Windows, it was a mess that bore little resemblance to the original.  It turns out that Portable Document Format files are not portable.

The fonts aren't embedded.  After a bit of looking on the interwebs, I discovered that one is supposed to use only 14 "standard" fonts, which are not guaranteed, and therefore not standard--and besides, they're pretty limited.  So the only alternative is to embed.  The Interwebs says no problem, I can just use Adobe Acrobat or something.  Right.

The question is, *how* do I embed fonts from LibreOffice (or any other open-source application, for that matter)?  And how do I know which fonts are open and legally unencumbered?  In this document I have used Gentium and Comic Sans, for example.  Surely there's a Linux way to do this right.

---

### Post by Impavidus on 2018-01-25
I can't find an option for it in LibreOffice (version 5.4.2.2, the standard in Ubuntu 17.10), but I created a test document and exported it to pdf format (using the Archive PDF/A-1a (ISO 19005-1) option, but that doesn't seem to matter) and opened the pdf in evince (aka document viewer, the default pdf viewer). File -> properties -> fonts tells me all fonts are either standard or embedded, specifically the only font I used is partially embedded (that is, only the characters actually used). So it seems that LibreOffice should embed the fonts by default. Can you check what evince tells you about the fonts in that pdf?

---

### Post by Holger_Gehrke on 2018-01-25
When exporting from LibreOffice as PDF you have to set the option to export as "PDF/A-1a (ISO 19005-1)-Archive". This produces a variant of the PDF-format meant for long-time archival storage of documents with all non-standard fonts (partially,only used glyphs) embedded and with tags to make the structure of the document accessible. You can expect to produce rather large files that way. Printing to a pdf file can also embed fonts (just checked by printing this page from Firefox into a file and checking the fonts tab in the file properties dialog of evince).

For the fonts distributed through the ubuntu repositories the legal situation is made clear by documents that get installed along with the fonts that you'll often find in subdirectories of /usr/share/docs whose name begins with 'fonts-' , for example the license for the dejavu-core fonts can be found in the file '/usr/share/doc/fonts-dejavu-core/copyright'. For other fonts you'll have to find out yourself what you're allowed to do with them and what not.

Holger

---

### Post by Dennis N on 2018-01-25
> The question is, how do I embed fonts from Libre Office (or any other open-source application, for that matter)?

In LibreOffice, did you try  **File > Properties > Font > checkbox: "embed fonts in the document"** and then **File > Export as PDF**?

---

### Post by Holger_Gehrke on 2018-01-25
> **Dennis N said:**
> In LibreOffice, did you try  **File > Properties > Font > checkbox: "embed fonts in the document"** and then **File > Export as PDF**?

That embeds the fonts in the OpenDocumentText file. If you run 'unzip -l "Name of ODT-File.odt" ' you'll see that there's several ttf-files in there. It doesn't embed the fonts in the pdf, unless you use the "PDF/A" variant, which will embed the fonts no matter what that setting says.

Holger

---

### Post by Dennis N on 2018-01-25
> **Holger_Gehrke said:**
> That embeds the fonts in the OpenDocumentText file. If you run 'unzip -l "Name of ODT-File.odt" ' you'll see that there's several ttf-files in there. It doesn't embed the fonts in the pdf, unless you use the "PDF/A" variant, which will embed the fonts no matter what that setting says.

Holger

My exported PDFs used the embedded fonts. so I would only say it worked for me.

---

### Post by VanillaMozilla on 2018-01-25
Thanks very much!  I'm impressed by the prompt and 100% correct responses.

The problem is solved, although in an unexpected way.  As far as I can tell, LibreOffice embeds the fonts in the PDF file by default.  For some unknown reason the process failed once, although I thought the work flow was identical on both Linux and Windows.  I can't duplicate the problem, and I don't know if I have the original file.

For the record, specifying PDF/A-1a is supposed to enforce embedding of fonts, although LibreOffice seems to do it by default.

I could not set LibreOffice to embed fonts in the .odt files by default, but it is possible to automatically get a choice when saving files:  Tools>Options>Load/Save>"Edit document properties before saving" .

---

