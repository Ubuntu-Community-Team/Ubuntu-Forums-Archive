---
title: "Not in Ubuntu, Wel in Windows!"
date: 2006-10-24
forum: General Help
---

### Post by linux-beginner on 2006-10-24
Hello,

The blow script doesn't run in my Ubuntu but wel in a windows system.
```
<?php
header("Content-type: image/png");

$image=imagecreate(400,200);
$red=imagecolorallocate($image,255,0,0);
$blue=imagecolorallocate($image,0,0,255);
$font="tahoma.ttf";

imageTTFtext($image, 50,0,20, 100, $blue,$font, "Test!");
imagepng($image);
?>
```

If I run it, I get this error message:
'The image "http://localhost/***" cannot be displayed,because it contians errors'.
Cuold you guide me, please?

Thanks,

---

### Post by mssever on 2006-10-24
In what ways is the output of phpinfo() different on the two systems? You might have different extentions loaded. Also, check the PHP manual on the functions in question for any system notes. I haven't used those particular functions (assuming they're PHP functions, not user functions, in which case it would be nice to post the function definitions as well), so I can't give specifics.

---

### Post by linux-beginner on 2006-10-24
I think it depends to configuration of php on my Ubuntu. The TrueType fonts are not configured for php in Ubuntu (I think) by default.
Do you know how I can compile my php so that php knows the fonts?

---

### Post by mssever on 2006-10-24
Do you have php5-gd installed (or php4-gd)? In general, it's much better to use the version from Synaptic/apt-get than to compile it yourself. You might want to look through synaptic for some php pachages that you need.

If you still want to compile PHP, you need to install several packages. Assuming that you're running apache2-mpm-prefork, you need apache2-prefork-dev. If you're running a different Apache, you need the appropriate dev package that provides apxs2. Assuming the above, do ```
sudo apt-get install apache2-mpm-prefork-dev build-essential
```

Next, read [http://www.php.net/manual/en/install.unix.php](http://www.php.net/manual/en/install.unix.php) and [http://www.php.net/manual/en/install.unix.apache2.php](http://www.php.net/manual/en/install.unix.apache2.php). You'll need to look in the various manual sections for the appropriate ./configure options for the appropriate libs. Also, ./configure --help will probably have some information.

EDIT: TrueType fonts work in other programs in Ubuntu out of the box, so I'm sure that TTF support is present in PHP, as well.

---

### Post by linux-beginner on 2006-10-24
I'v got apache2 with php5 on my computer. I couldn't find a packge in Synaptic with witch my problem can get solved. 
I've installed these two package from Synaptick "pache2-mpm-prefork" and "apache2-prefork-dev". 
What I don't undrestand is that if I type "./configure --help" in my terminal I get this message: bash: "./configure: No such file or directory".
What is going on?!

---

### Post by mssever on 2006-10-24
First, if you're going to compile your own PHP, remove all the php stuff from Synaptic. By the way, you should be reasonably proficient with the command line if you try to compile. Download the PHP source tarball. cd to the directory you saved the tarball to. Type ```
tar xjvf tarballname
``` Replace j with z in you downloaded the gz version instead of the bz2 one. cd to the dir created by extracting the tarball. Now, you can do ./configure, being sure to use the proper options. Take special care to adjust any paths to reflect your setup. If you don't have a file referenced, fix that before continuing.

Once configure runs without any errors, type ```
make && sudo make install
```I don't know if the source tarball automatically configures PHP to start on boot. You might need to make a bootscript in /etc/init.d and symlink it in /etc/rc[2-5].d

---

