---
title: "htdocs dir w/ apache2 ubuntu package"
date: 2006-12-20
forum: General Help
---

### Post by maddog39 on 2006-12-20
Hello all,

I just installed the apache2 package from synaptic and I ran:
```
find / htdocs
```
and it turned up with nothing found, so where the heck is the htdocs folder. Anyone know? When going to localhost everything works fine, I get the default page with directory listing. So I know its working.

Thanks!
-maddog39

---

### Post by Nathaniel on 2006-12-20
it's in /var/www by default

or you could create a folder called "public_html" in your home-directory and access it through http://localhost/~<your username>

---

### Post by maddog39 on 2006-12-20
Oh okay, thanks alot then. There's no XAMPP for PowerPC so I reverted to using the ubuntu repos.

---

