---
title: "LibreOffice chokes on 47 page document"
date: 2018-12-14
forum: General Help
---

### Post by Bartender on 2018-12-14
I've got a 47 page document called "PC Notes".  Saved in .odt.  It's a record of problems and fixes over several years of running Ubuntu.  The doc has followed me across two or three PC's.

The problem is that Libre locks up for a few minutes every time I try to scan down to the end of the document, or try to go back to the beginning from the end.  I went into Tools>Options>LibreOffice and turned Memory up to 1GB for Libre and 256 MB per object.

That didn't help.  Libre still hangs up for a minute or two if I try to scroll thru the document.  There are screen shots and links here and there in the document and I wonder if that's what's causing it to hang?  

I tried making a copy of the doc and renaming it.  That didn't make any difference.

Anyone got any ideas?

---

### Post by DuckHook on 2018-12-14
You may have a corrupted .odt file. First thing: backup your document, perhaps twice, and one to off-disk USB stick or similar for extra safety. That way, you can work on one copy with assurance that if you bork it further, you can still start over.

FWIW, I practice a similar habit, recording fixes and customizations needed for new installs. Mine is about 20 pages long and has over 100 different items. I too would be very upset if I couldn't recover this file. So, I keep it as a plain text file rather than as an .odt. The more critical something is, the simpler I want it to be. The text file contains only link references to screen shots and sites.

You can try the following site to fix a corrupted .odt file: [https://online.officerecovery.com/writer/](https://online.officerecovery.com/writer/)

Note, however, that it is by OpenOffice and is run through your web browser using javascript. Libreoffice is a fork of OpenOffice which occurred so long ago that there may be some significant but subtle divergence in file formats. This is unlikely given that .odt is supposed to be an open "standard", but one never knows. If you can get past the OpenOffice taint, allowing their script to run in your browser and the possibility of incompatibility, you may wish to give this a try.

If, at some point, your file fails to open at all, you can try unzipping the .odt file and extracting the contents. .odt files are simply zipped files containing several file prongs dedicated to different functions. Your contents are in an .xml file named *contents.xml* that can be read in any text editor. Before you can unzip, you may have to copy and rename first. Example:```
cp document.odt document.zip
```You should be able to see your contents although it will be full of xml tags. But at least you will have your content.

You can also try the libreoffice forums: [https://ask.libreoffice.org/en/questions/](https://ask.libreoffice.org/en/questions/)

---

### Post by Bartender on 2018-12-15
Thanks for the help.

I forgot to mention that when Libre locks up, everything stops.  The PC won't respond to any inputs until Libre finally refreshes.  I don't know if that helps to point toward a resolution?

One thing I'm thinking about is cutting the doc into several pieces and see what happens.  I seem to be able to scroll thru about ten pages before it hangs.

---

### Post by rbmorse on 2018-12-15
First, what DuckHook said about backups. 

Let the document load fully then "save as" to a new name (as opposed to just making a copy of the file).   If you get a dialog box asking if you want to convert the document format to .odt (even though it is already .odt) select "yes".

---

### Post by ajgreeny on 2018-12-15
What size is the file; if it has many screenshots and images it may be huge, though I'm not sure why a large file with no other corruption should cause a problem.

What type of links are included in the document; are they just links to websites or similar, ie, URLs?

---

