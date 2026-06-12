---
title: "pdf backends and rendering quality; anything beating or equalling acrobat?"
date: 2008-07-01
forum: General Help
---

### Post by urlwolf on 2008-07-01
Hi,

It seems that there are different pdf backends and they have different rendering quality; 

Here's proof; same doc with adobe 9:
[http://www.flickr.com/photos/50799208@N00/2627421553/](http://www.flickr.com/photos/50799208@N00/2627421553/) 

And with okular:

[http://www.flickr.com/photos/50799208@N00/2627421523/](http://www.flickr.com/photos/50799208@N00/2627421523/)

anything beating or equalling acrobat? Okular enables you to get different pdf backends (defaults to ghostview). Maybe there are better ones?

Any help greatly appreciated. I spend many hours looking at pdfs on the screen, and small improvements in readability make a big difference.

---

### Post by urlwolf on 2008-07-01
*bump*...
I wonder if anyone here spent time comparing the rendering of different pdf engines.

It's a bit of a pity that to get the crispest quality I need to resort to adobe (which sucks in many other ways, i.e., memory consumption and not being open source).

THanks

---

### Post by django0909 on 2008-07-01
I used Open Office to render the pdf's for my final year degree stuff, and it all looked nice and tidy. Although for some reason it refuses to process the '-' character. Weird.

---

### Post by VMC on 2008-07-01
Yes I know, its hard to beat Adobe reader. Are you running this through Wine or just using it under Windows?

I have used FoxIT reader using Wine. It's better than the default, but Adobe has better fonts.

---

### Post by soccerboy on 2008-07-01
you could run adobe under linux.  It is available from adobe's site.  Or I use evince document reader and it has worked pretty well for me.

---

### Post by edm1 on 2008-07-01
as soccerboy said the native linux version is available [here]("http://www.adobe.com/products/acrobat/readstep2_allversions.html"). You'll be wanting the '.deb' version.

---

### Post by lswb on 2008-07-01
I've used evince and tried a few other OSS pdf viewers, but I just have to say that IMHO Adobe did an excellent job with their current linux version. (unlike their earlier linux offerings) It surpasses anything else I've tried when it comes to rendering a pdf document and having working internal links, table of contents, features, etc. It's available in the ubuntu repositores as well as a .deb directly from adobe.

---

### Post by soccerboy on 2008-07-01
If adobe can't do a good job on a spec that they wrote then that is just sad (kind of like their flash player)

---

### Post by kevdog on 2008-07-01
ghostscript or latex

---

### Post by urlwolf on 2008-07-02
Right, the problem is that I like to highlight pdfs, and you cannot do that with acrobat reader.

This is why okular is great for me. You can add notes and highlights... I'm a researcher so I read plenty of pdf papers over one day, and annotate them.

So ideally I'd like the rendering quality of adobe, but with the possibility of adding notes and highlights. That's Acrobat pro, but unfortunately there's no linux version for that, right? 

Oh, and I'm running ubuntu 64 bits. The installer from adobe (.deb) complained that it was the 32-bit version... 

Knowing how adobe and 64-bit linux don't mix well :) I'm afraid to ask... is there any workaround for this?

Thanks

---

### Post by urlwolf on 2008-07-02
> **kevdog said:**
> ghostscript or latex

to this (and django0909's post)...
I need to display pdfs someone else has created, not create my own.

---

### Post by urlwolf on 2008-07-02
Ok, so it looks like what we have is the following.
(1) if you want the best rendering engine, you have to use adobe's
(2) if you want to annotate pdfs, you need adobe acrobat, which is not available for linux

(3) adobe sucks at implementing their products on linux, more so in 64-bit architectures

Ergo: I'm condemned to use windows to read papers. Or Macs.
This is as dissapointing as it gets.

---

### Post by lswb on 2008-07-02
Take a look at pdfedit from the repositories or their homepage [http://pdfedit.petricek.net/index_e.html](http://pdfedit.petricek.net/index_e.html)

---

### Post by urlwolf on 2008-07-03
Thanks Iswb, I had found pdfedit myself.
While it looks like it packs great power (scriptability!), it doesn't solve the simpler problem of being able to read a pdf in an agile way (moving around a TOC, having a selection of views -facing, continuous, etc-).

The editing possibilities of pdfedit are awesome; but as a reader is so-so at best. I don't think you can do most basic display alternatives; It doesn't even have keyboard mappings for moving around the document. The interface is clearly designed to do deep work on one page a time, then display the next etc.

And unfortunately the rendering quality is exactly the same as Xpdf (the engine used!). So no, not a solution at all.

There's one crazy possibility: running acrobat 5 under wine. It's an ancient version, but the only one reported to work on the winedb site. Will try that.

Thanks

---

