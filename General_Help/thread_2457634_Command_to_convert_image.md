---
title: "Command to convert image"
date: 2021-02-05
forum: General Help
---

### Post by satimis on 2021-02-05
Hi,

How to use command converting an image```

Original - 657h	1199w pixels
New - 241h 777w pixels

```
Thanks

Regards

---

### Post by dinkidonk on 2021-02-06
If you have ffmpeg installed, you can use:

```
ffmpeg -i "input.jpg" -vf "scale=777:241:flags=lanczos" "output.jpg"
```

---

### Post by HermanAB on 2021-02-06
There is a utility called... wait for it... drum roll... big applause...
convert

$ man convert
Name
convert - convert between image formats as well as resize an image, blur, crop, despeckle, dither, draw on, flip, join, re-sample, and much more.
Synopsis

convert [input-options] input-file [output-options] output-file

Overview
The convert program is a member of the imagemagick(1) suite of tools. Use it to convert between image formats as well as resize an image, blur, crop, despeckle, dither, draw on, flip, join, re-sample, and much more.

For more information about the convert command, point your browser to file:///usr/share/doc/ImageMagick-6.5.4/www/convert.html or [http://www.imagemagick.org/script/convert.php](http://www.imagemagick.org/script/convert.php).

---

### Post by SeijiSensei on 2021-02-06
I usually do things like this using Gwenview or GIMP, but convert is another easy solution.

```
convert image.jpg -resize 241x777! new.jpg
```

The exclamation point indicates that the resizing should take place even if the aspect ratio of the new image differs from the old.

See, for instance, [https://www.digitalocean.com/community/tutorials/workflow-resizing-images-with-imagemagick](https://www.digitalocean.com/community/tutorials/workflow-resizing-images-with-imagemagick)

convert is part of the Imagemagick suite. You can install it from the repositories with
```
sudo apt install imagemagick
```

---

