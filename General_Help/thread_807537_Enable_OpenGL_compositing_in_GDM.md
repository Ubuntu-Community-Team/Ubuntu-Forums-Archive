---
title: "Enable OpenGL compositing in GDM?"
date: 2008-05-25
forum: General Help
---

### Post by smartboyathome on 2008-05-25
Is there a flag you have to enable to be able to enable compositing? Or some other way? I thought it was supposed to be included with this last release of GNOME, but Ubuntu chose not to include it for maturity reasons.

---

### Post by Forlong on 2008-05-26
[http://live.gnome.org/GDM/2.22/Configuration](http://live.gnome.org/GDM/2.22/Configuration)

Seems like you'd have to add some gconf schemas for that.

---

### Post by smartboyathome on 2008-05-26
It seems that Ubuntu doesn't include the schemas files with GDM. Wonder why. :(

---

### Post by Forlong on 2008-05-26
Like I said, you'd have to add 'em yourself. But I investigated a little more and it seems like this won't help either. If I understood it right, you'd have to recompile the particular application then to make it work.

As for Ubuntu not shipping those by default: originally, I thought it was because Ubuntu doesn't have the window based GDM anyway (on Ubuntu's default GDM, using Compiz wouldn't change a thing, since there's nothing to move around) but I checked with Arch Linux and they don't have these schemas either.

---

### Post by smartboyathome on 2008-05-26
I found out why. It is included with GDM 2.22, ubuntu ships with 2.20. If you install 2.22, you get schemas, but it didn't work for me and I have to reinstall 2.20. :(

---

