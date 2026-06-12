---
title: "Searching within pdf files from dash"
date: 2013-01-22
forum: General Help
---

### Post by Haur on 2013-01-22
I am just wondering if it is possible to search for words that are inside pdf files from the dash or some other location. 

If i can remember correctly this was enabled by default in OS X but on windows you had to download some special software from adobe.

Is there something compatible available for Ubuntu?

---

### Post by jonobr on 2013-01-22
Open to correction, I believe PDF cannot be searched directly.


You could use something like [pdftotext]("http://manpages.ubuntu.com/manpages/lucid/man1/pdftotext.1.html") and search that if your desperate!

---

### Post by Haur on 2013-01-22
Not really that desperate, but it is a useful feature, especially when you've got alot of big pdf documents. 

Does this mean that searching within files of any kind that contain text is not possible then?

---

### Post by jonobr on 2013-01-22
Found an interesting post [here ]("http://unix.stackexchange.com/questions/6704/grep-pdf-files")with a couple of good recommendations


One was doing pdf2text searching on the fly- Answer 12

Or using the pdfgrep and the expression

```
find /path -iname '*.pdf' -exec pdfgrep pattern {} +
```

---

### Post by Haur on 2013-01-22
Well pdfgrep did do the trick, that is it allowed me to search through multiple pdf files at once as well as displaying the text in the terminal output. So then i can identify the pdf file that contains the relevant information and open it. Thanks for unearthing that piece of information.

Now if i could just get it to index the data so that searching doesn't take so long :D

---

### Post by LewisTM on 2013-01-22
There's a simple solution for you: Recoll. It will index and search PDF files as well as other documents for you. It's in the repos.

If you add the Recoll PPA, you also get a lens for searching from within the Dash.
[http://www.lesbonscomptes.com/recoll/download.html](http://www.lesbonscomptes.com/recoll/download.html)

Cheers!

---

### Post by jonobr on 2013-01-22
sweet

---

### Post by Haur on 2013-01-22
Thank you :o

---

