---
title: "Imagemagick 6.3.x"
date: 2007-04-12
forum: General Help
---

### Post by iluminate on 2007-04-12
Hi,

From what I can see there is only version 6.2.3 available of imagemagick in apt.
Where can I find version 6.3.x?
I would rather not compile it myself of obvious reasons.

Cheers

---

### Post by justleen on 2007-04-12
if the version is not in the repositories,  and since there is no deb file available you'll have to compile it yourself, im afraid...

---

### Post by iluminate on 2007-04-13
Thanks mister for you answer. Have to use magickwand, and now not possible if I do not compile it myself....what a shame.
Peace

---

### Post by DJTurboToJo on 2007-07-25
Hey,

I just installed imagemagick 6.3.5.3. I'm no an expert in Linux but I think my version works fine.
It works on the command line and with its C API (MagickWand).

I deinstalled the old imageversion via Synaptic Package Manager.
Then I downloaded the newest source from [http://www.imagemagick.org/script/install-source.php](http://www.imagemagick.org/script/install-source.php)
Then do the unpack stuff  gunzip -c ImageMagick.tar.gz | tar xvf - and go in this new folder  cd ImageMagick-6.3.5
The next step is the configuration and this the crucial part. There is a lot you can configure (if you really want to know what s going on check: [http://www.imagemagick.org/script/advanced-unix-installation.php](http://www.imagemagick.org/script/advanced-unix-installation.php) for more information).

For me it was important that I change the prefix (./configure --prefix=/usr) this ensures that it gets installed in /usr and not in the default folder /usr/local. 
After that I did make and then sudo make install. During this installation there are many warnings messages like libtool: link: warning and then something like blablabla seems to be moved. This warning is triggered by the GNU libtool that complains about the // in the path. However the make runs through and after sudo make install I could use MagickWand.

So if you really need the newest version...try and install it.

Maybe that helps
TurboToJo

---

### Post by wayfarer_boy on 2008-01-10
An old thread, I know, but thanks to DJTurboToJo's tip, I now have an ImageMagick that can -extent using a specific background colour (only available in ImageMagick 6.3.2 or above)!  Thanks particularly  for the configure code:
```
./configure --prefix=/usr
```
Very handy!

---

### Post by dante.regis on 2008-02-14
Thanks for the help!

Just for notice, since I'm a lazy guy, I prefer typing an extra "z" on the tar command rather than using gunzip:

tar xvzf filename.tar.gz

instead of your (working) method: gunzip -c filename.tar.gz | tar xvf -

just a question of choice, yet though you should know

---

