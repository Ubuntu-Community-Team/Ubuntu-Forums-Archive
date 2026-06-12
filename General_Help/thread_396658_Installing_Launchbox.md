---
title: "Installing Launchbox"
date: 2007-03-29
forum: General Help
---

### Post by daz4126 on 2007-03-29
I'm trying to install [Gnome Launchbox]("http://developer.imendio.com/projects/gnome-launch-box") and get the following output when running ./configure:

```
No package 'gnome-vfs-2.0' found
No package 'libgnomeui-2.0' found
No package 'libgnome-menu' found
No package 'gnome-desktop-2.0' found
No package 'libebook-1.2' found
No package 'gconf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LB_CFLAGS
and LB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

Does anybody know what this means and how I could fix it? I've tried looking for some of those packages in synaptic and they aren't there!

thanks,

DAZ

---

### Post by solar george on 2007-03-29
The packages that you need will not have the exact same names as those mentioned in the configure script, you will need the -dev version as well.

For
> No package 'gnome-vfs-2.0' found

try installing 
```
libgnome-vfs-dev
```

---

### Post by daz4126 on 2007-03-29
thanks, but according to synaptic, that package doesn't exist either.

DAZ

---

### Post by solar george on 2007-03-29
Try this instead,

libgnomevfs2-dev


I just did an apt-cache search for vfs, you just need to look through the list and find one that seems to match what you need.

---

### Post by daz4126 on 2007-03-29
Thanks! I just installed my first program ever from source. There seemed to be loads of dependencies though, is that normal? 

This program is in early development, but could be good in the future. Not sure how it indexes all your files and programs though.

thanks again solar george!

DAZ

---

### Post by solar george on 2007-03-29
> There seemed to be loads of dependencies though, is that normal? 

Yes, to compile a program you need the -dev versions of the packages and ubuntu doesn't install them by default. All linux programs rely heavily on shared libraries of code to aviod reinventing the wheel.

---

### Post by daz4126 on 2007-03-29
so what is the difference between the packages and the -dev packages? I would have thought you only needed -dev packages to develop the program, not to use it.

DAZ

---

### Post by solar george on 2007-03-29
The -dev package includes the header files that are needed by programs during compilation whereas the ordinary package just installs the runtime files that are needed by programs during ordinary use.

---

