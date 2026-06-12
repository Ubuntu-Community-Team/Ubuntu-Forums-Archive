---
title: "how do I convert png to svg?"
date: 2007-01-13
forum: General Help
---

### Post by Coop on 2007-01-13
Hello
How do I convert a png picture to svg?I have Inkscape installed.
What do I do?Please reply to me.
Regards Coop.

---

### Post by peterLinux on 2007-01-13
AFAIK
The Import command supports all of the bitmap formats that are covered with GdkPixbuf
(Including PNG)
Export as SVG...

Peter

---

### Post by WiseElben on 2007-01-13
Or you can just install an SVG editor like Inkscape (available in the repos), import the PNG, and export it as SVG.

---

### Post by peterLinux on 2007-01-13
That's exactly what I mean or are you looking for a command line solution?

Not sure about this one but it may work, I have not checked the syntax of the command use at your own risk
inkscape -export-svg=new.svg newlogo2.png

I know the other way around from svg to png works that way

---

### Post by kakao on 2007-09-30
> **peterLinux said:**
> inkscape -export-svg=new.svg newlogo2.png

That option -export-svg does not exist and as I understand the man pages inkscape can not convert png to svg. Only the other way around (vector -> raster) would work (as you said already). Still, inkscape can *import* png (and other raster/pixel graphics) via the File menu and you than can trace it via the Path menu -> "Trace Bitmap...". In my tests with a small (48x48) png it didn't look good, though.

Cheers.

---

### Post by williamts99 on 2007-11-12
> **Coop said:**
> Hello
How do I convert a png picture to svg?I have Inkscape installed.
What do I do?Please reply to me.
Regards Coop.


The absolute best way that I have found to "Automatically" convert from png to svg is to use VectorMagic from Stanford.  [http://vectormagic.stanford.edu/](http://vectormagic.stanford.edu/)

I think you will be truly amazed at the results.
Let me know how it goes.

Best Regards,
Williamts99

---

### Post by mcduck on 2007-11-12
There is no simple way to convert from bitmap image format into vector image format.

The only thing you can do is import the image in some vector image editor (like Inkscape) and then try to trace it into vectors. The result will never be exactly same as your original bitmap image was, but it might be good enough for your needs.

To do this with Inkscape, import the PNG image into Inkscape, select it and then go to Path/Trace Bitmap. Then you just have to try different settings until you get a result that pleases you.

---

### Post by williamts99 on 2007-11-12
> **mcduck said:**
> There is no simple way to convert from bitmap image format into vector image format.
.


Talk about timing on a reply :-)

Seriously though, try out VectorMagic from Stanford. [http://vectormagic.stanford.edu/](http://vectormagic.stanford.edu/)

---

### Post by mcduck on 2007-11-12
> **williamts99 said:**
> Talk about timing on a reply :-)

Seriously though, try out VectorMagic from Stanford. [http://vectormagic.stanford.edu/](http://vectormagic.stanford.edu/)

Well, I admit, that is a simple, although the result, like with any other tool, is not the same as the original was. But that is the nature of vector graphics, and that web site was a nice one, Ill have to remember it in case I some day need to convert some images and I don't happen to have my laptop at hand :)

It's just that usually when people  wish to convert image from one format to other, they are expecting to get exactly the same image, only indifferent file format. And that's not possible when converting from bitmaps to vectors.

---

### Post by williamts99 on 2007-11-12
Good point, I figured that if they wanted to vectorize their images that they would know the result they wanted.  :-)

---

### Post by rsambuca on 2007-11-12
The best method is to trace the paths by hand.  It is the only way you can be efficient with your points and paths.

---

### Post by williamts99 on 2007-11-12
> **rsambuca said:**
> The best method is to trace the paths by hand.  It is the only way you can be efficient with your points and paths.

I should have said 'automatically', because it is true that tracing them by hand is the best, it is a lot of work, which I don't think that he was looking to do it by hand :-)

---

### Post by edutiao on 2008-03-09
> **mcduck said:**
> There is no simple way to convert from bitmap image format into vector image format.

The only thing you can do is import the image in some vector image editor (like Inkscape) and then try to trace it into vectors. The result will never be exactly same as your original bitmap image was, but it might be good enough for your needs.

To do this with Inkscape, import the PNG image into Inkscape, select it and then go to Path/Trace Bitmap. Then you just have to try different settings until you get a result that pleases you.
This path really helped. Is there any way to automate this bitmap tracing? inkscape trace icon.png icon.svg? :) I'm doing a buuf gnome icon theme and would really like the icons to be scalable...

---

### Post by all2ez on 2008-06-23
i found an answer from here and it worked for me:

[http://ubuntuforums.org/showthread.php?p=5245724](http://ubuntuforums.org/showthread.php?p=5245724)

> **odysseusjak said:**
> I'm not sure if this is still an issue, but I have found that the way I described above doesn't work.  I have since 'discovered' how to do it.

First, open a Terminal and paste

sudo apt-get install python-lxml

Press Enter and supply your password.

Once that's finished, open up the png in Inkscape.  From the 'Effects' menu, select 'Images' > 'Imbed all images'

A pop up will ask what you want to do, click 'Apply'.

Now, you can select 'Save As...' from the file menu and save your images as a SVG.

i didn't have to install the python thingy, the menu option just worked (there is a typo it is 'Embed all images')

---

