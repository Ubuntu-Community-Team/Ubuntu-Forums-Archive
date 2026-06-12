---
title: "Enabling GD in PHP5"
date: 2007-07-22
forum: General Help
---

### Post by somody on 2007-07-22
Hello,

I just set up a LAMP server on my Kubuntu box and installed a copy of MediaWiki.  There's a certain extension that can be used to plot graphs, which I thought would be very useful for the purposes of my wiki.  However, after installing it and attempting to embed a graph in an article, PHP always returns an error: ```
Fatal error: Call to undefined function imagepng() in /home/user/NSSWiki/extensions/WikiPlot/PlotClass/plot.class.php on line 756
```.

I contacted the creator of the extension to see what was happening through Google Code ([http://code.google.com/p/wikiplot/issues/detail?id=13](http://code.google.com/p/wikiplot/issues/detail?id=13)), and he said that, most likely, I didn't have GD installed.  So I installed that both from the repositories and from source, but it didn't make a difference.

According to the creator of the extension, it's probably just some wrong configuration to do with GD not being enabled or installed correctly.  He recommended that I create a thread here to ask for help.  Thanks!

--Christian Somody

---

### Post by fuzzyeric on 2007-08-28
In the category of "Is it plugged in?  Is it turned on?"...

Have you run
    apt-get install php5-gd

This should provide the glue between PHP and gd.

---

### Post by apetresc on 2007-08-28
Load this page into your web server: ```
<HTML>
<HEAD><TITLE>PHP INFO</TITLE></HEAD>
<BODY>
<?php phpinfo(); ?>
</BODY>
</HTML>

```
Check to see if, when you load this page, there is a section ```
gd
GD Support 	enabled
GD Version 	2.0 or higher
FreeType Support 	enabled
FreeType Linkage 	with freetype
FreeType Version 	2.1.7
T1Lib Support 	enabled
GIF Read Support 	enabled
GIF Create Support 	enabled
JPG Support 	enabled
PNG Support 	enabled
WBMP Support 	enabled
```

---

### Post by somody on 2007-09-04
I get this:

```
gd
GD Support 	enabled
GD Version 	2.0 or higher
FreeType Support 	enabled
FreeType Linkage 	with freetype
FreeType Version 	2.2.1
T1Lib Support 	enabled
GIF Read Support 	enabled
GIF Create Support 	enabled
JPG Support 	enabled
PNG Support 	enabled
WBMP Support 	enabled
```

---

### Post by apetresc on 2007-09-04
> **somody said:**
> I get this:

You're all set then; PHP does recognize your GD extension, and it is enabled. If you're having problems running things, it is almost certainly a problem with your code. If you'd like, post the code giving you trouble, what you expect the output to be, and I'll give it a look :)

---

### Post by jopsen on 2007-09-06
Hi,

It seams he still gets a:
Fatal error: Call to undefined function imageantialias() in
/home/christian/NSSWiki/test.php on line 5

When using the imageantialias() function... does it require anything special, isn't it available in php5 or what??

//Regards Jonas F. Jensen

---

### Post by dorgan on 2007-10-10
It seems I am also having this problem, and its just with imageantialias, i think it has to do with the install GD library.

---

### Post by mr_niceguy on 2008-02-13
[http://www.hostingforum.ca/804602-php-problem-gd-library.html](http://www.hostingforum.ca/804602-php-problem-gd-library.html)

Apparently if you install php from source with GD enabled this problem is solved. Would be better if the repos were updated.

Should we issue a request somewhere?

---

