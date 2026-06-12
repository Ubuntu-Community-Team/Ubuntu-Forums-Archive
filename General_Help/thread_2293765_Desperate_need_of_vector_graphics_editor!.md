---
title: "Desperate need of vector graphics editor!"
date: 2015-09-07
forum: General Help
---

### Post by jvanleuven on 2015-09-07
Hi,

I'm looking for a vector graphics editor that runs in Ubuntu. I currently use Inkscape, but it fails miserably (uses all the ram) when loading large files (~500,000 features).

Is anyone aware of any alternative software? Preferably it would utilize GPU acceleration, and of course run in linux.

I have a pretty good laptop. 16Gb ram, quad i7, 6Gb gpu. I can't really install Adobe illustrator on a windows/linux dual boot because my hard drives are set up in raid0.

Thanks,

James

---

### Post by ajgreeny on 2015-09-07
How large are those "large files" as it is hard to believe that scribus should use all 16GB of ram, and I wonder if there is something else going on here that is not directly associated simply with scribus.

Tell us more about your system hardware in detail as it may be related to that and perhaps whatever graphic driver you are using.  Is your system using optimus graphics, and if so do you have bumblebee installed and running?

---

### Post by jvanleuven on 2015-09-07
I appreciate the response.

I made a pdf file with Processing ([https://processing.org/](https://processing.org/)) and was trying to import into it into Inkscape. The pdf is 11Mb. If I only print out about 1/2 of the figure in the pdf, I can open it in Inkscape, but it is really slow, uses about 14Gb ram, and the saved *.svg file is 250Mb. 

Illustrator will open it (on a mac computer) but is is really slow too, and doesn't import correctly. 

I thought that Inkscape does not use the gpu, so I have had it turned off. I'll try with it on. Yep, optimus graphics running 355 drivers and nvidia prime.

I'm running Ubuntu 14.04 with the nightly updates of Inkscape. The computer has a i7-4860HQ processor with a GTX870M gpu. I'm running dual Evo850 ssd in raid0. 

Do you think a computer with more ram would help? I could potentially install Inkscape on our servers. 

Thanks.

---

### Post by Buntu Bunny on 2015-09-08
> **ajgreeny said:**
>  ... hard to believe that scribus should use all 16GB of ram,and I wonder if there is something else going on here that is not directly associated simply with scribus.

But he's asking about Inkscape. Apples and oranges.

jvanleuven, you might try the [InkscapeForum]("http://www.inkscapeforum.com/") for help too.

---

### Post by dragonfly41 on 2015-09-08
Try this ..

[https://code.google.com/p/svg-edit/](https://code.google.com/p/svg-edit/)

demo ..

[http://svg-edit.googlecode.com/svn/branches/stable/editor/svg-editor.html](http://svg-edit.googlecode.com/svn/branches/stable/editor/svg-editor.html)

---

### Post by ajgreeny on 2015-09-09
> **Buntu Bunny said:**
> But he's asking about Inkscape. Apples and oranges.

jvanleuven, you might try the [InkscapeForum]("http://www.inkscapeforum.com/") for help too.
Sorry, that was simply a typo!!

I am still surprised that inkscape (got it right this time!) would use all of the 16GB of ram on one image.

---

