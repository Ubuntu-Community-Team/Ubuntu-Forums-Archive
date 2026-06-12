---
title: "Using windows to download ubuntu packages"
date: 2008-05-09
forum: General Help
---

### Post by dm6257 on 2008-05-09
Does anyone know the procedure to download a package using windows and install it from a file?  ( I don't have an internet connection on Ubuntu 8.04 )

---

### Post by jimv on 2008-05-09
You can download packages here:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by didooofidooo on 2008-05-09
if you try to download packages and install it manually you will get mad from the dependency problems so i recommend you to fix the internet connection in Ubuntu it's so much easier and if you fail to do it use source codes compiling also

---

### Post by strabes on 2008-05-09
It is strongly recommended that you stick to packages located in the ubuntu repositories. If you must download a package that is not in the repositories, you can simply download any .deb file and double click on it inside ubuntu, just like an .exe file in windows.

> if you try to download packages and install it manually you will get mad from the dependency problems

This is not true. If you download a debian package (.deb), gdebi-gtk will install it and take care of all the dependencies.

---

### Post by gali98 on 2008-05-09
> **strabes said:**
> It is strongly recommended that you stick to packages located in the ubuntu repositories. If you must download a package that is not in the repositories, you can simply download any .deb file and double click on it inside ubuntu, just like an .exe file in windows.



This is not true. If you download a debian package (.deb), gdebi-gtk will install it and take care of all the dependencies.

Hmmm... well if you think about it, where do the dependencies come from. Trust me... doing it this way makes for a long night running between computers looking for stray dependencies, and it is easy to install wrong packages. Trust me, internet is the way to go if possible. I don't think I could go back.
Kory

---

### Post by nick09 on 2008-05-09
Try enabling roaming mode in ubuntu.

---

### Post by gali98 on 2008-05-09
> **nick09 said:**
> Try enabling roaming mode in ubuntu.

I'm not trying to be rude at all, but what does that have to do with anything?

---

### Post by dm6257 on 2008-05-10
Thanks to all.  Fixing the internet connection is the reason I needed the build-essential and linux-headers packages.  I was hoping I could download them onto a file and use apt-get or aptitude to install them.  From the instructions it seems like the installation utilities only work with internet connections.

---

### Post by sekinto on 2008-05-10
To install a local package you use:
```
dpkg -i [YOURPACKAGE]
```

---

