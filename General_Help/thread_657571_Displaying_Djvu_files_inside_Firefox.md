---
title: "Displaying Djvu files inside Firefox"
date: 2008-01-03
forum: General Help
---

### Post by Nonno Bassotto on 2008-01-03
I know that a djvu plugin for firefox exists, but I prefer to use evince for all my documents.

I'm trying to view Djvu files with evince inside Firefox, using mozplugger. I can use evince to look at pdf, ps and dvi files with it. So I tried to add the lines
```

image/vnd.djvu:djvu:Djvu file
image/djvu:djvu:Djvu file
	repeat noisy swallow(evince) fill: evince "$file"

```
to /etc/mozpluggerrc. This should be the analog of
```

application/pdf:pdf:PDF file
application/x-pdf:pdf:PDF file
text/pdf:pdf:PDF file
text/x-pdf:pdf:PDF file
	repeat swallow(acroread) fill: acroread7 -openInNewWindow "$file"
	repeat swallow(documentShell) fill: acroread5 -geometry +9000+9000 +useFrontEndProgram "$file"
	repeat noisy swallow(evince) fill: evince "$file"
	repeat noisy swallow(kpdf) fill: kpdf "$file"
	repeat noisy swallow(Xpdf) fill: xpdf -g +9000+9000 "$file"
	GV()

application/x-dvi:dvi:DVI file
	repeat noisy swallow(evince) fill: evince "$file"
        repeat swallow(kdvi) fill: kdvi "$file"
	repeat swallow(xdvi) fill: xdvi -safer -hush -geometry +9000+9000 "$file"

application/x-postscript:ps:PostScript file
application/postscript:ps:PostScript file
	GV()
	repeat noisy swallow(evince) fill: evince "$file"

```
if I understand correctly how this file is written. For instance adding the first line for dvi files (it was not there by default) allowed me to use evince instead of xdvi for dvi files.

But I had no luck up to now. Can anybody explain why?

---

### Post by Nonno Bassotto on 2008-01-04
Ehm... guess it's time to bump

---

