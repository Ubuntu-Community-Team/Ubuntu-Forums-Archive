---
title: "Grep Command"
date: 2022-05-16
forum: General Help
---

### Post by tombarnes on 2022-05-16
Hello,
my results for finding results with the grep command are strange: I've got files of customers in .odt and printed also in .pdf
when I write grep -r name /.../ the output is only of customers which files I've imported from another system and only when they were printed by PDFCreator. Files that contents the name but were written in .odt and/or printed into .pdf via libreOffice Writer aren't found.
So, I changed in some examples the permissions , then I thought the missing author in the metadata was the problem and changed them also, but now I wonder where to look or what to change for using 'grep'   - may someone could help. thx in advance

---

### Post by Impavidus on 2022-05-16
Not sure what exactly you're trying to do...

Grep deals with plain text files. It doesn't know how to handle every type of binary file in existence, so it can't read the information encoded in such files. Some binary files may store some strings in plain text in the file. PDF allows this and many PDF files have some lines with plain text, alternating with blocks of binary data. Grep may pick up such plain text lines and some PDF creaters create them (comments, metadata), but not all.

If you want to search for some string in some binary file, you need a tool that can read that file format. If this tool can convert it in plain text, you can use grep to search the plain text.

.odt is a zip-compressed xml file and xml is plain text, so you could unzip the .odt file and pipe the result though grep. It should provide grep with readable strings, but there will be some xml-tags mixed through.

---

### Post by Holger_Gehrke on 2022-05-16
'grep' is very much a tool for searching in plain text files. 'odt' files are actually zip files filled with compressed XML, CSS and other stuff. The actual text-content is in a file named content.xml inside the odt. So to grep in an odt you'd do something like
```

unzip -p myfile.odt content.xml|grep 'searchpattern'

```
And who knows what evil lurks in the heart of PDF :confused: ... PDF is really not a text format, it's more a multi-page vector and bitmap graphics format with the ability to have text somewhere in there and lots of different options for compressing or otherwise mangling the content. There are tools to pull the text out of a pdf like 'pdftotext' from the package poppler-utils.
```

pdftotext myfile.pdf -|grep 'searchpattern'

```

A bit of scripting to loop over the files you want to search and suppress the output of all the failed searches is left as an exercise to the reader ;)

Holger

---

### Post by TheFu on 2022-05-16
grep isn't a generic, read-any-file, search.  It is only for plain text.  If you want to search non-text files, then you'll need to use other tools.

Also, PDF files can just be an image shoved into the PDF container.  There isn't any useful text there, so no search tool will find anything in those types of PDFs.  You may be able to use OCR to "read" the image and generate text, but OCR is usually pretty terrible.  I've seen about 80% accuracy most of the time, which means that the words you are likely to search won't be found.

ODT is a compressed XML file. Again - not text.

The way that most of the search tools work is to have helper applications that handle different, specific, file types when they index the files.  I use **Recoll**, but there are others.  **sudo apt install recoll**, then run the GUI, configure where to look for stuff you want indexed, ensure any helper tools are also installed, then have it index all the files.  From there, you can use the GUI or CLI interface to search.

---

### Post by tombarnes on 2022-05-16
Thanks for these informations - but if my files whether .odt or .pdf named by the search attribute in the grep command it should work. For example: the file's name is Sandman.pdf - and my command ist grep -r "Sandman" /directory/ - then it shouldn't be a problem. Am I wrong? It isn't a word within a file I'm looking for.

---

### Post by tombarnes on 2022-05-16
And what is confusing me also is the fact, that files that were made in Ubuntu with LibreOffice whether .odt and .pdf weren't found

---

### Post by #&amp;thj^% on 2022-05-16
yep as TheFu points out grep won't work on those. ( .odt and .pdf )
have a look here: [https://askubuntu.com/questions/938834/grep-for-text-in-odt-or-doc-files](https://askubuntu.com/questions/938834/grep-for-text-in-odt-or-doc-files)
might help you.

---

### Post by Holger_Gehrke on 2022-05-16
'grep' is for searching inside text files (or standard input). Searching for filenames is done with locate (simple) or find (very complex but extremely powerful). 
'grep -r "Sandman" /directory/' would search for the string 'Sandman' in the content of all files in /directory/ and its sub-directories.

Holger

---

### Post by tombarnes on 2022-05-16
Thanks 1fallen for the link. I read it and now I understand. 
I shouldn't be that persistent while working with grep. I was so eager finding a solution on that. 
I wasn't aware of the fact that with .odt and .pdf I'm handling with binary an / or compressed files. Now I understand.
Thx to all of u

---

### Post by TheFu on 2022-05-16
If you want to search just on filenames, use **locate** or **find**.  Those don't look *_inside_* the files, just at the names.

Recoll will look at both the names and the contents, provided the contents can be parsed.  Again, if the PDF files are just images, then no search tool can do anything.  For PDF wrapped around images, my best suggestion is to fully fill out the metadata and perhaps run some OCR to generate 80% accurate text which can be placed **under** the images.  gscan2pdf can do this.  While it can be connected to a scanner, run OCR, then put the text under the scanned image, it can also be used with a PDF file directly.  After you do the OCR, take a look at the results, as text, so you get a feel for the accuracy.

---

### Post by Impavidus on 2022-05-16
PDF is very good for the purpose for which it was designed: describing documents for printing. If you want to do something other than printing or reading the document on screen and you have access to the source from which the pdf was generated, use that. PDF was never designed to be editable or to allow the computer to extract any information from it other than what it should look like on paper.

---

### Post by dragonfly41 on 2022-05-16
This might help ..

[https://github.com/phiresky/ripgrep-all](https://github.com/phiresky/ripgrep-all)

---

### Post by #&amp;thj^% on 2022-05-16
> **dragonfly41 said:**
> This might help ..

[https://github.com/phiresky/ripgrep-all](https://github.com/phiresky/ripgrep-all)

That's a keeper for me, almost addicting. :D

---

### Post by tombarnes on 2022-05-16
Thanks. Again...I thought I already sent my gratitude to all of u.
And  my last notification was that after reading the link of 1fallen I now  understood, that I was handling with binary and / or compressed files.
I was a little bit stubborn I have to say...misunderstanding the grep command.

---

### Post by #&amp;thj^% on 2022-05-16
You can mark it SOLVED in your first post, top right corner "Thread Tools"
don't be so hard on yourself we've all been hyper-focused at least once. ;)

---

