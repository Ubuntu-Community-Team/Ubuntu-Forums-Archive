---
title: "Want jpeg support in gd image library and php?"
date: 2012-10-24
forum: General Help
---

### Post by Randy Schilling on 2012-10-24
My application (which is Coppermine Photo Gallery) is generating this error:

Fatal error: Call to undefined function imagecreatefromjpeg() in /usr/local/apache2/htdocs/rjs357/cpg/install.php on line 2145

I corrected a similar such error with gif by adding --with-gd to the ./configure
command of my php installation.  Here I followed the instructions from

[http://www.php.net/manual/en/image.installation.php](http://www.php.net/manual/en/image.installation.php)                  (*)

This added a "gd table" to my phpinfo page.  That table shows that gif, png,
wbmp, and xbm are enabled but says nothing for jpeg.  
There is another table that says that gd.jpeg_ignore_warning has local value 0
and master value 0.  I don't know what this means.

Synaptic tells me that various libjpegs are installed.
(Don't know how or when these were installed.)
My reference (*) suggests that I should include --with-jpeg-dir=DIR
in the ./configure command of my php installation.

Is this correct and what should I use for the value of DIR?

Thanks for taking time for this - Randy

---

