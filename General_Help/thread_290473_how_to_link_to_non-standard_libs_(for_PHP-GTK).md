---
title: "how to link to non-standard libs (for PHP-GTK)"
date: 2006-11-01
forum: General Help
---

### Post by pixelpusher on 2006-11-01
Hi, I have a lovely working edgy system but trying to build PHP-GTK2 requires glib-2.6.* and gtk-2.6.*

1st off I downloaded from gtk.org and compiled glib-2.6.0 , configure, make, make install all went fine but even though pkg-config says I have glib 2.6 the actual .so is still 2.1.4.

I found I could link the /usr/lib/libglib.2.so.0 to the 2.6 version installed in /usr/local/lib but after that many gnome apps would not work I assume because of the wrong lib version (restoring the original link made everything work again).

I am quite green at this sort of stuff... any pointers on how to use and link to say glib-2.6 for php-gtk compilation but still keep the 2.1.4 libs for normal use.... I saw in ./configure --help that I could set LDFLAGS ... but really not sure howto.

Any help appreciated & if anyone has php-gtk2 to build on dapper or edgy .. please share :)

---

