---
title: "Problem with .epub format in abiword to calibre"
date: 2012-11-15
forum: General Help
---

### Post by Matthewexeter on 2012-11-15
Hello I am looking to write some ebooks.
I have exported a few pages, each with a short amount of text on them as .epub format.
This is to test the export and review it in calibre.
When I load my test piece in calibre, there are no separate pages, where in abiword they were on separate pages.
Does anyone know what I am missing here, thanks

---

### Post by cjhabs on 2012-11-15
The reader device should handle breaking the data into pages - the page breaks and line breaks will vary with the form factor of the reading device. Have a look at the ebook in something like fbreader

---

### Post by Matthewexeter on 2012-11-19
I have tried reading the .epub exports from abiword in calibre(an ebook read and converter), twice.
One with page breaks for each page, and one without.
In both documents the pages were spaced out on seperate pages in the document.
In this example I was putting a short poem on each page so the text was not filling up the pages.

Still all the text was glued together without the spacing.

Should I take this to the abiword or epub forums?

---

### Post by Matthewexeter on 2012-11-22
I have found a solution to this.
A program called sigil. It is an ebook editor just like jutoh only free. 
However it is not as standard in the ubuntu studio repository. This is a shame.

[http://code.google.com/p/sigil/](http://code.google.com/p/sigil/) the home page

[https://launchpad.net/~rgibert/+archive/ebook]("https://launchpad.net/%7Ergibert/+archive/ebook") for the repository information.

---

### Post by mastablasta on 2012-11-22
yup Sigil is the one you need. and yes too bad it's not in the repositories. 
 
Otherwise you could try Libre office and then move it to epub and edit it in sigil.

---

### Post by Matthewexeter on 2012-11-23
@mastablasta Yeah thats what I was trying to do in abiword.
From my little experience I would argue that for the sake of ebooks it would be best to work direct from sigil. Unless of course one would have work already done in abiword/libreofiice/etc.
Although for now I am writing a collection of poems, so I am putting one poem per html section.
It would be allot easier with stories to put it into sections, say per chapter than plcing one poem per section.

---

