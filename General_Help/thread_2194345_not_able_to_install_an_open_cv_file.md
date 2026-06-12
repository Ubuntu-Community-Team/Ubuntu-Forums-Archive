---
title: "not able to install an open cv file"
date: 2013-12-17
forum: General Help
---

### Post by vikas.180 on 2013-12-17
hi everyone i am trying to install opencv on ubuntu at some time i had to run the following command 
vikas@vikas-Pavilion:~$ sudo apt-get install libjpeg-prog

but i am getting the following error 


Reading package lists... Done
Building dependency tree... 0%
Building dependency tree       
Reading state information... Done
E: Unable to locate package libjpeg-prog

what am i supposed to do to fix this please help as i am a newbie to linux

---

### Post by tgalati4 on 2013-12-17
Panic!

No, you need not panic.  You are missing a library.  Why don't you see if the library exists in the repositories:

Open a terminal:

```
apt-cache search libjpeg-prog
```

I might look like:


tgalati4@tpad-Gloria7 ~ $ apt-cache search libjpeg-prog
libjpeg-progs - Programs for manipulating JPEG files
imgsizer - Adds WIDTH and HEIGHT attributes to IMG tags in HTML files

If you see it, then try installing it:

```
sudo apt-get install libjpeg-progs
```

I'm on an older, Jaunty system, so you may have *prog or *progs, which is why you have to check yourself.

Then try installing *opencv* again.

A Haiku for your situation:

Install fails.  Missing?
Apt-cache search and there it is.
Try installing now.

---

### Post by deadflowr on 2013-12-17
> [COLOR=#000000]I'm on an older, Jaunty system, so you may have *prog or *progs, which is why you have to check yourself.[/COLOR]
I'm on precise right now and it's progs here.

So, there that's.
?

---

### Post by vikas.180 on 2013-12-17
Thanks a lot worked i have a similar problem with 

vikas@vikas-Pavilion:~$ sudo apt-get install libavformat52
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libavformat52
vikas@vikas-Pavilion:~$

---

### Post by deadflowr on 2013-12-18
> **vikas.180 said:**
> Thanks a lot worked i have a similar problem with 

vikas@vikas-Pavilion:~$ sudo apt-get install libavformat52
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libavformat52
vikas@vikas-Pavilion:~$

It always helps for us to know what version of Ubuntu you are on.
I see this package is available on Ubuntu for lucid and lucid only
[http://packages.ubuntu.com/search?keywords=libavformat52](http://packages.ubuntu.com/search?keywords=libavformat52)

I'm sure the package for newer versions have a different name, or something along those lines.
I see on precise I have libavformat53 packages available, if that helps...

---

### Post by QIII on 2013-12-18
*Moved to **General Help***

---

