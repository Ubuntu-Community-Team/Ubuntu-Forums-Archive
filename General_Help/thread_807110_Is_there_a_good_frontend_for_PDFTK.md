---
title: "Is there a good frontend for PDFTK ?"
date: 2008-05-25
forum: General Help
---

### Post by frenchn00b on 2008-05-25
Is there a good frontend for PDFTK ? 

Something bit like in windows : [http://www.portablefreeware.com/graphics/guipdftk/screenshot.gif](http://www.portablefreeware.com/graphics/guipdftk/screenshot.gif)

Regards

---

### Post by noynac on 2008-05-27
A few weeks ago, I did a search for a frontend for PDFtk but couldn't find one. Lacking an alternative, I use Nautilus Actions in connection with PDFtk and Ghostscript. In this way, I can, for example, highlight multiple files, right-click, and select combine. Splitting one PDF into individual pages is equally easy. This is not as good as a dedicated GUI, but it works for now.

---

### Post by frenchn00b on 2008-05-28
> **noynac said:**
> A few weeks ago, I did a search for a frontend for PDFtk but couldn't find one. Lacking an alternative, I use Nautilus Actions in connection with PDFtk and Ghostscript. In this way, I can, for example, highlight multiple files, right-click, and select combine. Splitting one PDF into individual pages is equally easy. This is not as good as a dedicated GUI, but it works for now.


Thank you, well It's better than nothing. 
 
And how did you install this into Nautilus, since I never find out this... sounds cool

---

### Post by noynac on 2008-05-28
> **frenchn00b said:**
> Thank you, well It's better than nothing. And how did you install this into Nautilus, since I never find out this... sounds cool

Nautilus-actions is in the repo's. After installation, the Nautilus-actions applet is accessed from the *System > Preferences* menu.

The best way to learn how to construct a configuration (i.e. action) is to import and view some that other have done. The following page has many "configurations" to get you started:

[http://www.grumz.net/index.php?q=configlist](http://www.grumz.net/index.php?q=configlist)

By way of example, the following is the meat-and-potatoes part of my combine-pdf configuration. It does require Ghostscript. 

* Label: Combine PDF

* Path: /usr/bin/gs

* Parameters: -sDEVICE=pdfwrite -dNOPAUSE -dQUIET -dBATCH -sOutputFile=%d/combined.pdf %M

* Filenames: *.pdf

* Mimetypes: *.*

* Appears if selection has multiple files or folders: check mark this.

After doing the above, right-click after selecting two or more PDF files in Nautilus, and left-click on Combine PDF. The new, combined PDF file will have the name combined.pdf. 

I hope this doesn't sound overly complicated--it's really quite simple once you get the hang of it.

---

### Post by claypole on 2008-10-06
Try this [http://www.paehl.de/pdf/gui_pdftk.html](http://www.paehl.de/pdf/gui_pdftk.html)

:)

---

### Post by msisamonopoly on 2008-11-04
> **noynac said:**
> Nautilus-actions is in the repo's. After installation, the Nautilus-actions applet is accessed from the *System > Preferences* menu.

The best way to learn how to construct a configuration (i.e. action) is to import and view some that other have done. The following page has many "configurations" to get you started:

[http://www.grumz.net/index.php?q=configlist](http://www.grumz.net/index.php?q=configlist)

By way of example, the following is the meat-and-potatoes part of my combine-pdf configuration. It does require Ghostscript. 

* Label: Combine PDF

* Path: /usr/bin/gs

* Parameters: -sDEVICE=pdfwrite -dNOPAUSE -dQUIET -dBATCH -sOutputFile=%d/combined.pdf %M

* Filenames: *.pdf

* Mimetypes: *.*

* Appears if selection has multiple files or folders: check mark this.

After doing the above, right-click after selecting two or more PDF files in Nautilus, and left-click on Combine PDF. The new, combined PDF file will have the name combined.pdf. 

I hope this doesn't sound overly complicated--it's really quite simple once you get the hang of it.

noynac - Nautilus Actions is great. I got this working. Have one question, is there a way to determine the order in which the files are combined?

No matter the order I select the files, they always get combined in the same order. However I would like to be able to control which one comes first, or second, or third, etc.

Any suggestions?

---

### Post by kaibob on 2008-11-04
> **msisamonopoly said:**
> noynac - Nautilus Actions is great. I got this working. Have one question, is there a way to determine the order in which the files are combined?
msisamonopoly

I don't know of any easy way to do this. You could write a shell script that allows you to set the file order and then have this script called by Nautilus Actions, but that would be a kludge and not what you want. Perhaps someone else will have an idea. 

Kaibob (previously known as noyac)

---

### Post by canakas on 2009-06-11
Hello everyone,

Thanks to you Kaibob! This was exactly what I needed...

I combine tens of pdfs every week (articles + supporting information) before I stick them into my bibtex file... this is so much easier than using GS from the command line...

By the way... the order of the files in nautilus is coherent to the order they are passed to gs through %M... so the dirtiest hack is to sort on some term that gives you the order you want and the mark the files and right click...:-$ 
luckily sorting by name usually gives med the order I need.... (xx000000.pdf and xx000000_something.pdf)

-canakas

---

### Post by Mujaheiden on 2009-06-25
does anybody get the gui pdftk to work?

---

### Post by tazztone on 2009-11-27
> **Mujaheiden said:**
> does anybody get the gui pdftk to work?
yes see this thread : [http://ubuntuforums.org/showthread.php?t=1266402&highlight=pdftk](http://ubuntuforums.org/showthread.php?t=1266402&highlight=pdftk)

---

