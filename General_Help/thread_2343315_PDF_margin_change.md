---
title: "PDF margin change?"
date: 2016-11-15
forum: General Help
---

### Post by PDA1 on 2016-11-15
Presently I'm using PDFCrop to trim off excess margins around a pdf consisting of about 48 pages, letter size.  The resulting file prints and looks perfect except that I need specific margins for binding in a book.  As there are many pages to be changed I don't want to have to separate the file into individual pages and make the change.

I need to be able to alternately provide a defined margin for the right margin of one page and then left margin of another page.  All of this is within one PDF consisting of many pages.

Example-  page 1- Right margin 1/2" (or whatever value needed....pts, pixels)
                page 2- Left margin 1/2" (or whatever value needed....pts, pixels)

Folks, I'm gettin' pretty old and time is money and very precious.  So, unless you know exactly how to do this don't reply.

---

### Post by HermanAB on 2016-11-15
It can be done with convert.

I can tell you exactly how too: Read the man page.
:)

---

### Post by PDA1 on 2016-11-15
What is "convert"?

Man pages are typically useless- written by techy types with no ability to explain it to us mortals.

---

### Post by QIII on 2016-11-15
Hello!

One may, of course, read the man page and then, armed with a few questions, return to this thread for further assistance.

Please don't make demands on the form of response you receive.  Such conditions are not likely to move people to rush to your aid.

---

### Post by PDA1 on 2016-11-15
I wouldn't waste you time with replies that don't answer the question (except this one of course).

The first reply above was useless written by someone not interested in helping.  Thus, time wasted.

If you don't like what or how I asked the question then you need not reply.

---

### Post by HermanAB on 2016-11-15
Interesting, not a single person even bothered to look at the convert man page.  Image Magick is a very good program.  It is installed by default on pretty much every Linux machine for many good reasons and I'm not going to read the man page for you...

---

### Post by PDA1 on 2016-11-15
'Just took a look at the "man". 

Too vague and confusing and certainly not written for regular non-tech people.

---

### Post by steeldriver on 2016-11-15
I think the approach I'd take is this:


[LIST=1]
[*]split the original pdf into odd and even pages 
[*]apply pdfcrop separately to the odd and even page files, with L and R margins as appropriate 
[*]recombine the pages into a single document 
[/LIST]

You can use pdftk to do the split and recombine. So for example

```
$ pdftk somefile.pdf cat 1-endeven output even.pdf
$ pdftk somefile.pdf cat 1-endodd output odd.pdf

```

```
$ pdfcrop --margins "40 0 0 0" odd.pdf
PDFCROP 1.20, 2009/10/06 - Copyright (c) 2002-2009 by Heiko Oberdiek.
==> 7 pages written on `odd-crop.pdf'.
$ 
$ pdfcrop --margins "0 0 40 0" even.pdf
PDFCROP 1.20, 2009/10/06 - Copyright (c) 2002-2009 by Heiko Oberdiek.
==> 7 pages written on `even-crop.pdf'.

```

```
$ pdftk odd-crop.pdf even-crop.pdf shuffle output newfile.pdf
```

Another option might be to use the **pdfbook **command from the **pdfjam **package - however I have no experience with that, and I can't find a decent example of its usage.

---

### Post by PDA1 on 2016-11-15
You are brilliant.

Perfect approach, clearly explained. It works!  

Thank you!

---

### Post by HermanAB on 2016-11-15
How to handle margin and paging problems for the google impaired:

[https://imagemagick.org/discourse-server/viewtopic.php?t=26545](https://imagemagick.org/discourse-server/viewtopic.php?t=26545)

[http://www.imagemagick.org/Usage/crop/](http://www.imagemagick.org/Usage/crop/)

---

### Post by QIII on 2016-11-15
OK.  I think we're done here.

Closed.

---

