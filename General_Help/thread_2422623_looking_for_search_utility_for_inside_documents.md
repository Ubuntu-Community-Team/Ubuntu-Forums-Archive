---
title: "looking for search utility for inside documents"
date: 2019-07-10
forum: General Help
---

### Post by oilyfish on 2019-07-10
To search inside  documents in .Doc  .DocX  and .ODT  for character  strings
 The search utilities I've fund  will only find filenames
Know of any ?
It'd be real sweet if there was one with  Boolean capability

---

### Post by Ralph L on 2019-07-10
Is Libre Office Writer not sufficient???

---

### Post by HermanAB on 2019-07-10
grep of course, but +1 for LbreOffice Writer, if you are scared of the command line.

---

### Post by Impavidus on 2019-07-11
grep is the search tool to use for plain text files, but .doc, .docx and .odt are very complex file formats. As far as I know, only libreoffice writer (or similar office suites) knows how to deal with them. So you need a search tool inside libreoffice writer. I think there is a search function, but I don't know if it can loop automatically through a number of files.

.odt is a zip archive containing a bunch of files, one of which is contents.xml, which contains the contents of the document in plain text format, mixed with formatting, links to images etc. in xml format. You may be able to write a script to search them. For .doc and .docx, I doubt it will be so simple.

---

### Post by dragonfly41 on 2019-07-11
I use ripgrep for batch scanning files other than .doc, .docx and .odt .. [but searching around I came across this]("https://www.linuxuprising.com/2019/06/rga-search-text-in-pdf-ebooks-office.html") .. rga

I have not tried it but it looks promising.

Another approach is to use pandoc file conversion in some form of batch processing script or python.

.docx and .odt can be seen as input formats here [(scroll down)]("https://pandoc.org/")

The idea is that the pandoc conversion is piped through ripgrep.

---

### Post by Holger_Gehrke on 2019-07-11
The new MS-Office *.???x file formats are actually very similar to the OpenOffice *.od?; both are zip-archives full of xml. The file with the text-content in a Word .docx is named 'word/document.xml'. The difference between the formats are the names of the files inside the archive and the markup used.

Holger

---

### Post by oilyfish on 2019-07-12
I stumbled across RECOLL  I'm giving that a try.

---

