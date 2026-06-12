---
title: "Inkscape .svg in Linux to Coreldraw .cdr in Windows"
date: 2014-05-23
forum: General Help
---

### Post by ddubbz1979 on 2014-05-23
Trying to save files in Inkscape as .eps, .pdf, .svg etc isn't allowing me to open them in Coreldraw x4.  Copy and pasting yields best results but edges of graphics come out choppy and crooked without anything close to as clean of a look that are originally in Inkscape.  Any fix for this out there?  Thanks in advance.

---

### Post by ddubbz1979 on 2014-05-24
Still looking for a fix if anyone else has run into a similar issue.  Thanks.

---

### Post by dragonfly41 on 2014-05-24
I'm always interested in svg topics ... although I don't use Corel Draw ..

My first thought was to search for a "svg2cdr" library

There is in Ubuntu Software Centre "universal vector graphics translator (debug extension)" for the sk1 engine (see below)

and looking for "svg2cdr" led to this ...

[http://sk1project.org/modules.php?name=Products&product=uniconvertor](http://sk1project.org/modules.php?name=Products&product=uniconvertor) 

[http://sk1project.org/modules.php?name=Products&product=cdrexplorer](http://sk1project.org/modules.php?name=Products&product=cdrexplorer)

The latter tool might help in analysing the differences in file formats in Corel Draw.

...

This site gives more ideas ..

[http://www.ellipsys.org/blog/index.php?/archives/35-How-to-convert-CorelDRAW-files-to-open-formats.html&serendipity](http://www.ellipsys.org/blog/index.php?/archives/35-How-to-convert-CorelDRAW-files-to-open-formats.html&serendipity)[entrypage]=all&serendipity[entrypage]=all&serendipity[entrypage]=all


However these tools offer import of Corel Draw cdr to translate/convert to openformat svg.

I don't yet see how to import svg or sk1 into Corel Draw.


This thread refers to Corel having issues in importing svg ...

[http://community.coreldraw.com/forums/t/23740.aspx?PageIndex=2](http://community.coreldraw.com/forums/t/23740.aspx?PageIndex=2)

and suggests Inkscape > export svg to PDF > import PDF to Corel Draw.

---

### Post by ddubbz1979 on 2014-05-24
Thanks for the response.  I've tried the PDF route and to no benefit.  I get a scribbled looking graphic that looks like just an outline.  Copy and paste worked best but lost some quality in the transfer.  I know Corel will handle .svg but looks like it won't from Inkscape.

---

### Post by dragonfly41 on 2014-05-24
Inkscape should export well formed svg but you could try Xara Xtreme or Libre Office Draw  ...

p.s. or even Scribus.

[color=maroon]
Later edit ...

I would create a very basic test file (e.g. a square box) in both Corel Draw and Inkscape.

Save test file as svg from both Corel Draw and Inkscape.

Try also saving "optimised svg" from Inkscape.

In Ubuntu install Meld Diff Viewer.

Compare files using Meld to look for svg coding differences.
[/color]

---

