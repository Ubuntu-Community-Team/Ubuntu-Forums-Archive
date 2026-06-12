---
title: "Compiling GIMP 2.4, GLIB errors"
date: 2007-10-31
forum: General Help
---

### Post by Jimmey on 2007-10-31
I have tried to install GIMP 2.4 on Feisty following [this guide.]("https://help.ubuntu.com/community/GIMP2.4-on-Feisty")

However, when I try to compile GTK ( having already compiled GLIB), it says:
```

checking for GLIB - version >= 2.12.0... 
*** 'pkg-config --modversion glib-2.0' returned 2.14.2, but GLIB (2.12.11)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.12.0 or better is required. The latest version of
*** GLIB is always available from ftp://ftp.gtk.org/pub/gtk/.

```

Removing the old Glib would probably break my system as there are so many packages that rely on it, so does anyone know how I could resolve this issue~?

Thanks

---

### Post by Baloon on 2007-12-25
I am also facing the same problem. I am using Ubuntu Fiesty 7.10 and  the GIMP available in Ubuntu repo is 2.4.0.rc3. I need to upgrade to 2.4.3. So how do I resolve this GLIB problem.

Thanks in advance

---

### Post by geraldm on 2007-12-25
Jimmey and Baloon:
Please update your post by stating what happened after you have completed the suggestions that were provided in the error message in your post.  If those suggestions did not work, please so state.

Gerald

---

### Post by jespdj on 2007-12-25
If you're just looking for a newer version of GIMP, then have a look at [www.getdeb.net](www.getdeb.net) where you can get GIMP 2.4.2: [http://www.getdeb.net/app.php?name=Gimp](http://www.getdeb.net/app.php?name=Gimp)

---

### Post by articpenguin on 2007-12-25
did you install glib dev from synaptic?

---

### Post by ellgor on 2007-12-27
Hi,

I have exactly the same issue as you, if I could fix it I wouldn't be asking, let me know if you get a solution. 

regards, Ellgor

---

