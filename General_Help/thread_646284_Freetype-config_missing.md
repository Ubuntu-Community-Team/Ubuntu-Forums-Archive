---
title: "Freetype-config missing"
date: 2007-12-21
forum: General Help
---

### Post by resprung on 2007-12-21
Hiya!

I'm trying to install the "Ming" .swf output library for PHP -- on Ubuntu 6.06.

The ./config chokes with this error:

```
checking for freetype-config... no
configure: error: You must have freetype installed; see http://www.freetype.org/
```

But I *have* Freetype 2 installed:

```
ii libfreetype6   2.1.10-1ubuntu FreeType 2 font engine, shared library files
```

I've searched, and there is no "freetype-config" directory or file anywhere in my installation.

Help will be very much appreciated! :-D

---

### Post by shirilover on 2007-12-21
You need to install libfreetype6-dev.

---

### Post by resprung on 2007-12-21
Thanks!

For anyone else missing

```
usr/bin/freetype-config
```

You just need to apt-get the development freetype on top of your already installed libfreetype6:

```
apt-get install libfreetype6-dev
```

:)

---

