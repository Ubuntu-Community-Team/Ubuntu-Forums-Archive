---
title: "Problems installing debian package created with chekinstall"
date: 2007-05-21
forum: General Help
---

### Post by loathsome on 2007-05-21
Hi there,

EVERY SINGLE TIME I try to install a .deb file created by checkinstall, I get an error that looks like this; ```
 trying to overwrite `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so', which is a
lso in package libgconf2-4
dpkg-deb: subprocess paste killed by signal (Broken pipe)

```

In this case I'm trying to create one out of the Pidgin 2.0.0 source.

What is this? 

Thanks,
loathsome

---

### Post by loathsome on 2007-05-21
Just tried this with avant-window-navigator as well, and got this

```
dpkg: error processing /home/loathsome/Desktop/avant-window-navigator-0.1.1/avan
t-window-navigator_0.1.1-1_i386.deb (--install):
 trying to overwrite `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so', which is a
lso in package libgconf2-4
dpkg-deb: subprocess paste killed by signal (Broken pipe)

```

What the heck is this?

---

### Post by dannyboy79 on 2007-05-21
I had trouble compiling also, not sure why??? BUT there is already a pidgin 2.0 deb file out there. I found it here: 
[http://rapidshare.com/files/29533296/pidgin_2.0.0-1_i386.deb.html](http://rapidshare.com/files/29533296/pidgin_2.0.0-1_i386.deb.html)
[http://rapidshare.com/files/29536788/pidgin-otr_3.0.0-1_i386.deb.html](http://rapidshare.com/files/29536788/pidgin-otr_3.0.0-1_i386.deb.html)

or here:
[http://www.gnome-look.org/content/show.php/Pidgin+2+DEB?content=57356](http://www.gnome-look.org/content/show.php/Pidgin+2+DEB?content=57356)

or here:
[http://shortbrain.org/vinc-files/debs/im/](http://shortbrain.org/vinc-files/debs/im/)

---

### Post by loathsome on 2007-05-21
Hi,

Thanks - I know about the deb-files, that's not the point :)

---

### Post by dannyboy79 on 2007-05-21
i agree, I hate it when stuff doesn't work the way it is suppose to but there's a point in which it becomes a waste of time to figure out why something isn't working especially when there is another method that does work. (just my opinion)

---

### Post by loathsome on 2007-05-21
Yeah, I also agree - I always download deb-packages, but what if there's no other option? What if I have to compile? There's why having a working checkinstall would be terrfic.

:)

---

### Post by dannyboy79 on 2007-05-21
well I believe that checkinstall assums somethings about your system and whatnot. Did you send an email to the developer of the program? [http://checkinstall.izto.org/mailing-lists.php](http://checkinstall.izto.org/mailing-lists.php)

---

### Post by loathsome on 2007-05-22
No, I didn't - thanks for the tip.

I might do it if I don't figure this out soon :)

---

### Post by loathsome on 2007-05-22
[IMG]http://www.pcbsd.es/images/userphotos/Tuxy.jpg[/IMG]

Tuxx bumps this thread!

---

