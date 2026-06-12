---
title: "Image converter"
date: 2013-02-01
forum: General Help
---

### Post by hatewindows on 2013-02-01
Hello i just wanted to know if anyone knows of a free image converter for ubuntu 12.10  i have a Gif image and i'd like to convert it and save it to a jpg image.. Thanks for any help!

---

### Post by JKyleOKC on 2013-02-01
The program known as "gimp" (GNU Image Manipulation Program) has that capability. Simply open the GIF file, then from the menu select "File -> Save as ..." and select the file type to save as, then change the filename appropriately.

It's not the only program that can do the conversion, but it's the simplest I know of for the purpose. There's a whole suite of command-line tools called ImageMagick that do such things but it's a bit more complex to operate...

---

### Post by hatewindows on 2013-02-01
Thank you so much JKyleOKC

---

### Post by SeijiSensei on 2013-02-01
For many conversions, Imagemagick is simplicity itself.  Install the package with "sudo apt-get install imagemagick" then navigate to the folder where the images are stored and run 

```

cd /path/to/your/image/directory
convert file.gif file.jpg

```

That's it.  You can apply pretty much any conversion you want to the file as well.  For instance, here's the command to reduce the height and width by 50%:

```
convert -scale '50%' file.gif file.jpg
```

For the full nitty-gritty, visit [this page](http://www.imagemagick.org/script/convert.php).

---

### Post by gifford on 2013-02-01
Converseen is quick and easy.
[http://www.noobslab.com/2012/02/install-converseen-image-converter-on.html](http://www.noobslab.com/2012/02/install-converseen-image-converter-on.html)

---

### Post by ibjsb4 on 2013-02-02
Got some hits here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=convert+.gif+to+.jpg&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=convert+.gif+to+.jpg&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by howefield on 2013-02-02
Gimp would do it very well but is a bit of a sledgehammer to crack a nut approach, and you may find you would need to use the "Export to" rather than the "Save As" option.

+1 imagemagick

---

### Post by raja.genupula on 2013-02-02
> **SeijiSensei said:**
> For many conversions, Imagemagick is simplicity itself.  Install the package with "sudo apt-get install imagemagick" then navigate to the folder where the images are stored and run 

```

cd /path/to/your/image/directory
convert file.gif file.jpg

```That's it.  You can apply pretty much any conversion you want to the file as well.  For instance, here's the command to reduce the height and width by 50%:

```
convert -scale '50%' file.gif file.jpg
```For the full nitty-gritty, visit [this page]("http://www.imagemagick.org/script/convert.php").

+1 to convert.

you can play with many images by using *for* command in bash scripting .

---

