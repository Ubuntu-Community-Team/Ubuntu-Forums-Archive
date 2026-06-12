---
title: "command to change logo color"
date: 2017-12-14
forum: General Help
---

### Post by satimis on 2017-12-14
Hi all,

I have a logo in red color (pls see attached png file) with transparent background.

Is there a command line to change the color from red to yellow?  Please advise.  Thanks

Regards
satimis

---

### Post by vasa1 on 2017-12-14
Something like what is described in [https://www.imagemagick.org/discourse-server/viewtopic.php?p=69489&sid=820d9c8a0366a41c114491fd1f394151#p69489](https://www.imagemagick.org/discourse-server/viewtopic.php?p=69489&sid=820d9c8a0366a41c114491fd1f394151#p69489) maybe?

---

### Post by satimis on 2017-12-14
> **vasa1 said:**
> Something like what is described in [https://www.imagemagick.org/discourse-server/viewtopic.php?p=69489&sid=820d9c8a0366a41c114491fd1f394151#p69489](https://www.imagemagick.org/discourse-server/viewtopic.php?p=69489&sid=820d9c8a0366a41c114491fd1f394151#p69489) maybe?

Thanks for your link.

Following command helps me out:```

&#10219; convert traces_of_life_10_en.png -fuzz 15% -fill yellow -opa
que "#c03030" traces_of_life_10_en_yellow.png

```

I found it on Internet

Could you please help me to understand;
-fuzz 15%
-opaque "#c03030"
?

The background of the original image is transparent which is retained in the resulting image

Thanks

satimis

---

### Post by vasa1 on 2017-12-14
I don't have much successful experience with *convert*! I hope someone who knows better comes along.

---

### Post by again? on 2017-12-14
> **satimis said:**
> Thanks for your link.

Following command helps me out:```

&#10219; convert traces_of_life_10_en.png -fuzz 15% -fill yellow -opa
que "#c03030" traces_of_life_10_en_yellow.png

```

I found it on Internet

Could you please help me to understand;
-fuzz 15%
-opaque "#c03030"
?

The background of the original image is transparent which is retained in the resulting image

Thanks

satimis
**-opaque "#c03030"** is replacing the colour #c03030
**-fuzz 15%** allows for slight variations in the colour to replace. Edges are often darker.
eg -fuzz 15% leaves a reddish edge from original image.
[ATTACH=CONFIG]277830[/ATTACH]

Whereas increasing to -fuzz 75%, mostly eliminates the darker edge colour.
[ATTACH=CONFIG]277831[/ATTACH]

Have a read @ imagemagick.org
[http://www.imagemagick.org/Usage/color_basics/#fuzz](http://www.imagemagick.org/Usage/color_basics/#fuzz)
[http://www.imagemagick.org/Usage/color_basics/#opaque](http://www.imagemagick.org/Usage/color_basics/#opaque)

You should also have this local doc file you can open in your web browser.
file:///usr/share/doc/imagemagick-6-common/html/www/convert.html

---

### Post by leunam12 on 2017-12-14
It is easier to install Gimp or Pinta and use the Hue-Saturation tool to make your changes visually until you are satisfied with the result. Why do you want a command line solution, are you on a server with no graphical interface?

---

### Post by satimis on 2017-12-14
> **guber2 said:**
> **-opaque "#c03030"** is replacing the colour #c03030
**-fuzz 15%** allows for slight variations in the colour to replace. Edges are often darker.
eg -fuzz 15% leaves a reddish edge from original image.
[ATTACH=CONFIG]277830[/ATTACH]

Whereas increasing to -fuzz 75%, mostly eliminates the darker edge colour.
[ATTACH=CONFIG]277831[/ATTACH]

Have a read @ imagemagick.org
[http://www.imagemagick.org/Usage/color_basics/#fuzz](http://www.imagemagick.org/Usage/color_basics/#fuzz)
[http://www.imagemagick.org/Usage/color_basics/#opaque](http://www.imagemagick.org/Usage/color_basics/#opaque)

You should also have this local doc file you can open in your web browser.
file:///usr/share/doc/imagemagick-6-common/html/www/convert.html
Hi,

Thanks for your advice

I found the command line on Internet;

```

$ convert imput_file.png -fuzz 15% -fill '#xxxx' -opaque "#c03030" output_file.png

```

Only changed ```

'#xxxx'

``` 
to yellow and input and output filenames

Then it worked for me.  I have no idea about ```

-opaque "#c03030"

```

However the command didn't work on file traces_of_life_10_zh_transp.png (see attached file)
```

$ convert traces_of_life_10_zh_transp.png -fuzz 15% -fill red -opaque "#c03030" traces_of_life_10_zh_transp_red.png

```

I have to changing 15% to 100% then it works for me.  I don't know why?
traces_of_life_10_zh_transp.png is also a logo with transparent background.

```

file:///usr/share/doc/imagemagick-6-common/html/www/convert.html

```
File not found

$ convert --version```

Version: ImageMagick 6.8.9-9 Q16 x86_64 2017-07-31 http://www.imagemagick.org
Copyright: Copyright (C) 1999-2014 ImageMagick Studio LLC
Features: DPC Modules OpenMP
Delegates: bzlib cairo djvu fftw fontconfig freetype jbig jng jpeg lcms lqr ltdl lzma openexr pangocairo png rsvg tiff wmf x xml zlib

```

Regards
satimis

---

### Post by satimis on 2017-12-14
> **leunam12 said:**
> It is easier to install Gimp or Pinta and use the Hue-Saturation tool to make your changes visually until you are satisfied with the result. Why do you want a command line solution, are you on a server with no graphical interface?
Hi,

Thanks for your advice.

I haven't run GIMP and PhotoShop for prolonged time.  I think a command line would be easier for me to do this simple job.

Regards
satimis

---

### Post by again? on 2017-12-14
With the green coloured image you need to find the hex number of the colour you want to change and use this as the -opaque value.
[ATTACH=CONFIG]277840[/ATTACH]

"-fuzz 100%" will match all variations of color.
 It works with your image because there is only one colour in the image.

eg using this image with 2 colours.
[ATTACH=CONFIG]277842[/ATTACH]

If I want to change the blue colour I find out it's hex value(**#4578ef**).
[ATTACH=CONFIG]277844[/ATTACH]
and use this command to change that colour to red
```
convert python-icon.png -fuzz 15% -fill "red" -opaque "**#4578ef**" python-icon-red.png
```
[ATTACH=CONFIG]277843[/ATTACH]

If I used -fuzz 100% it would change all colours to red.
[ATTACH=CONFIG]277845[/ATTACH]

---

### Post by satimis on 2017-12-14
> **guber2 said:**
> With the green coloured image you need to find the hex number of the colour you want to change and use this as the -opaque value.
[ATTACH=CONFIG]277840[/ATTACH]

"-fuzz 100%" will match all variations of color.
 It works with your image because there is only one colour in the image.

eg using this image with 2 colours.
[ATTACH=CONFIG]277842[/ATTACH]

If I want to change the blue colour I find out it's hex value(**#4578ef**).
[ATTACH=CONFIG]277844[/ATTACH]
and use this command to change that colour to red
```
convert python-icon.png -fuzz 15% -fill "red" -opaque "**#4578ef**" python-icon-red.png
```
[ATTACH=CONFIG]277843[/ATTACH]

If I used -fuzz 100% it would change all colours to red.
[ATTACH=CONFIG]277845[/ATTACH]

Hi,

Thanks for your detail advice.

How to find the color code of my  logo?  Use gpick or GColor2?

Regards
satimis

---

### Post by again? on 2017-12-15
gcolor2 is easiest.
Click on the eye dropper in gcolor2  then the colour in your image.
If the image you are converting only has one colour the -opaque value doesn't really matter. Just use -fuzz 100% to convert all colours.

---

### Post by vasa1 on 2017-12-15
AFAICT, gcolor2 won't be in 18.04 which is a pity :(

gpick is still there.

---

### Post by satimis on 2017-12-15
> **guber2 said:**
> gcolor2 is easiest.
Click on the eye dropper in gcolor2  then the colour in your image.
If the image you are converting only has one colour the -opaque value doesn't really matter. Just use -fuzz 100% to convert all colours.
Hi,

Just got gcolor2 installed.  It is super easy to use.  Thanks

satimis

---

### Post by satimis on 2017-12-15
> **vasa1 said:**
> AFAICT, gcolor2 won't be in 18.04 which is a pity :(

gpick is still there.

Thanks for your information.  We'll see what will happen.  Maybe when 18.04 published there'll be a new package.

Regards
satimis

---

### Post by vasa1 on 2017-12-15
> **satimis said:**
> Re.
```

file:///usr/share/doc/imagemagick-6-common/html/www/convert.html

```
File not found
...
It may not be present by default but after you successfully run```
sudo apt-get install imagemagick-doc
```
the file (along with a lot more stuff) will be available.

---

### Post by satimis on 2017-12-16
> **vasa1 said:**
> It may not be present by default but after you successfully run```
sudo apt-get install imagemagick-doc
```
the file (along with a lot more stuff) will be available.
Performed following steps;

&#10219; convert --version```

Version: ImageMagick 6.8.9-9 Q16 x86_64 2017-07-31 http://www.imagemagick.org
Copyright: Copyright (C) 1999-2014 ImageMagick Studio LLC
Features: DPC Modules OpenMP
Delegates: bzlib cairo djvu fftw fontconfig freetype jbig jng jpeg lcms lqr ltdl lzma openexr pangocairo png rsvg tiff wmf x xml zlib

```


&#10219; sudo apt install imagemagick-doc```

.....
Processing triggers for doc-base (0.10.7) ...
Processing 1 added doc-base file...
Setting up libjs-jquery (1.11.3+dfsg-4) ...
Setting up imagemagick-doc (8:6.8.9.9-7ubuntu5.9) ...
Setting up javascript-common (11) ...
Setting up libjs-jquery-easing (10-2ubuntu2) ...
Setting up libjs-jquery-mousewheel (10-2ubuntu2) ...
Setting up libjs-jquery-fancybox (10-2ubuntu2) ...

```

on browser ran
file:///usr/share/doc/imagemagick-6-common/html/www/convert.html 
```

Firefox can’t find the file at /usr/share/doc/imagemagick-6-common/html/www/convert.html.

    Check the file name for capitalization or other typing errors.
    Check to see if the file was moved, renamed or deleted.

```


file:///usr/share/doc/imagemagick-6.8.9.9-common/html/www/convert.html
```

Firefox can’t find the file at /usr/share/doc/imagemagick-6.8.9.9-common/html/www/convert.html.

    Check the file name for capitalization or other typing errors.
    Check to see if the file was moved, renamed or deleted.

```

satimis

---

### Post by vasa1 on 2017-12-16
What does```
locate convert.html
```show?

But please run```
sudo updatedb
```first.

I see```
$ locate convert.html
/usr/share/doc/imagemagick-doc/www/convert.html
$ 
```on 16.04.

And this works on 16.04:```
file:///usr/share/doc/imagemagick-doc/www/convert.html
```

On 18.04, *locate convert.html* shows:```
$ locate convert.html
/usr/share/doc/imagemagick-6-common/html/www/convert.html
$ 
```

---

### Post by dragonfly41 on 2017-12-16
In my /usr/share/docs  .. Ubuntu 16.04
convert.html is found in /usr/share/doc/imagemagick-doc/www/convert.html

...

Incidentally another approach is to use Inkscape to create your logo, save as logo.svg, embed in your page and dynamically change font colour.
I did not find the font you are using, but MathJax_Fraktur is close.

---

### Post by satimis on 2017-12-16
> **vasa1 said:**
> What does```
locate convert.html
```show?

But please run```
sudo updatedb
```first.

I see```
$ locate convert.html
/usr/share/doc/imagemagick-doc/www/convert.html
$ 
```on 16.04.

And this works on 16.04:```
file:///usr/share/doc/imagemagick-doc/www/convert.html
```

On 18.04, *locate convert.html* shows:```
$ locate convert.html
/usr/share/doc/imagemagick-6-common/html/www/convert.html
$ 
```

On browser
file:///usr/share/doc/imagemagick-doc/www/convert.html```

ImageMagick Convert Command-line Tool
....

```
please see attached file screenshot_imagemagick.png

On Terminal
&#10219; locate convert.html
no output

&#10219; sudo find / -name convert.html```

[sudo] password for satimis: 
find: ‘/run/user/1000/gvfs’: Permission denied
/usr/share/doc/imagemagick-doc/www/convert.html
find: ‘/proc/8912’: No such file or directory
find: ‘/proc/8913’: No such file or directory
find: ‘/proc/8914’: No such file or directory
find: ‘/proc/8915’: No such file or directory
find: ‘/proc/8920’: No such file or directory

```

satimis

---

### Post by dragonfly41 on 2017-12-16
For the first attempt probably you did not run
sudo updatedb
before trying locate.
p.s. it may take some minutes to updatedb and locate.

For the second attempt try
sudo find / -type f -name convert.html
p.s. you may still see some permission errors.

---

### Post by satimis on 2017-12-17
> **dragonfly41 said:**
> For the first attempt probably you did not run
sudo updatedb
before trying locate.
p.s. it may take some minutes to updatedb and locate.

For the second attempt try
sudo find / -type f -name convert.html
p.s. you may still see some permission errors.
&#10219; sudo updatedb
[sudo] password for satimis: 
immediately pop without output

&#10219; locate convert.html```

/usr/share/doc/imagemagick-doc/www/convert.html

```

&#10219; sudo find / -type f -name convert.html```

find: ‘/run/user/1000/gvfs’: Permission denied
/usr/share/doc/imagemagick-doc/www/convert.html

```

Thanks

satimis

---

