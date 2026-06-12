---
title: "Batch resize 100 images by the inches."
date: 2013-10-30
forum: General Help
---

### Post by vap1485 on 2013-10-30
after scanning the images in 600 DPI the images are now 43.861x68.861
I want to resize them to 5.5x8.5

I tried to resize by percentage but that did not give me the size I wanted. Is there a mogrify command to scale down or resize by a certain percentage?

---

### Post by Vaphell on 2013-10-30
you can give a bounding box instead of percentage, eg -scale 5500x8500
that said your numbers are slighly off so don't expect exactly that size
43861/5500 = 7.97
68861/8500 = 8.10

given it's roughly 1/8, -scale 12.5% doesn't work properly?

---

### Post by vap1485 on 2013-10-30
12.5% made the image become 2.158x3.388

---

### Post by Vaphell on 2013-10-31
you can check the expected size of the result with something like this
```
$ convert test.gif **-set oldsize '%wx%h'** -scale 12.5% **-format '%[oldsize] => %wx%h' info:**
386x386 => 48x48
```

---

### Post by HiImTye on 2013-10-31
[http://www.imagemagick.org/script/command-line-processing.php#geometry](http://www.imagemagick.org/script/command-line-processing.php#geometry)
you can use a maximum value for either dimension, in pixels, and imagemagick will preserve the aspect ratio for you. just specify the maximum values you want

note: you are going to need to know how many pixels per inch you're printing at, and then do a little bit of math to get the pixel count. you can use the terminal for this, as well. just multiply the [COLOR=#006400]DPI[/COLOR] by the amount of [COLOR=#008080]inches[/COLOR] and you will have your pixel count, i.e. (for a 300 DPI printer at [COLOR=#daa520]5.5 inches wide[/COLOR] and [COLOR=#800080]8.5 inches tall[/COLOR]):
```
[ tye@t: ~ ]$ echo [COLOR=#008080]5.5[/COLOR]*[COLOR=#006400]300[/COLOR] | bc                                           
[COLOR=#daa520]1650[/COLOR].0
[ tye@t: ~ ]$ echo [COLOR=#008080]8.5[/COLOR]*[COLOR=#006400]300[/COLOR] | bc
[COLOR=#800080]2550[/COLOR].0
```
then feed this to imagemagick
```
for f in /path/to/folder/*.{jpg,bmp,png}; do convert "$f" -resize [COLOR=#daa520]1650[/COLOR]x[COLOR=#800080]2550[/COLOR] /output/path/"${f##*/}"; done
```and viola!

---

