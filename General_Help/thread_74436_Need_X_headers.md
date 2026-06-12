---
title: "Need X headers"
date: 2005-10-11
forum: General Help
---

### Post by siennalizard on 2005-10-11
To complete an installation of the Tk module for perl, it seems I need the xorg headers. The directory that should contain them seems not to (/usr/X11R6/include). Tk itself is installed, and I've been using the CPAN shell to initiate the install with "install Tk".

I'd be grateful for any suggestions and can provide as much information as necessary. Is is simply the case that a package needs installing? I've searched the repositories for "headers", but didn't find what I wanted.

Kind regards,
J.

---

### Post by mlomker on 2005-10-11
Try downloading **xlibs-dev**.  Whenever you are compiling something it is looking for the package that ends in -dev.

---

### Post by meanmrmustard on 2006-09-16
It's been a long time.... I just found this and am wondering if it worked or not.

---

