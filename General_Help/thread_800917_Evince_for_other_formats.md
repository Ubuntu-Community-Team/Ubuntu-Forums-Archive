---
title: "Evince for other formats?"
date: 2008-05-20
forum: General Help
---

### Post by MattKemp on 2008-05-20
Interesting point - I can't find a 'Productivity' forum on here anywhere.

To the point at hand - does anyone know of any document viewers similar to evince for other formats, such as .doc or .xls? I know I can open these in OpenOffice, but usually I just need a quick bit of information out of a Word document, not a full-on editor.

Essentially I'm looking for a read-only 'preview' mode for .docs. Does anyone know anything that would do this? Barring that, does anyone know of any specifications for office formats regarding presentation? If you can't find it, build it yourself, I guess.

Thanks,

-MK

---

### Post by ryanhaigh on 2008-05-20
This doesn't exactly fit what you were after but there is an application in the repos called wv, it has the capacity to convert word docs to other formats such as pdf as well as viewing summary information or just converting to RTF.

It not read only but abiword may be a lot faster at loading the doc, there is also a spreadsheet application called gnumeric however I have never used it so can't offer any advice on speed. You may want to check the man pages for these apps and see if there is a read-only flag that you can pass.

---

### Post by MattKemp on 2008-05-20
Thanks for the info.

Unfortunately it looks like evince [isn't interested]("http://mail.gnome.org/archives/desktop-devel-list/2005-April/msg00159.html") in providing the support itself. I'd still love the option - I'll keep people posted if anything ever comes about for this.

-MK

---

### Post by ryanhaigh on 2008-05-20
You could create a simple script that uses one of the applications in the wv package to convert the word document to a pdf in the /tmp directory and open it with whatever pdf viewer is installed. Whether this is satisfactory will depend on how good a job wv does with the conversion and the speed. From a breif google search it seem nautilus passes the filename as the first arguement to the called application so your script could be something like:

```

#!/bin/bash
#script to convert word doc to pdf and open in viewer


#convert the doc to pdf

wvpdf $1 /tmp/converted_doc.pdf

#use gnome-open to open the pdf in whatever is the default viewer

gnome-open /tmp/converted_doc.pdf

exit

```
xdg-open may be better than gnome-open as it is independant of desktop environment but i don't know if its installed by default, its part of the xdg-utils package.

---

