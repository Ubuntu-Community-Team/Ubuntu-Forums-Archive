---
title: "Need help installing tea text editor 14.1 on dapper"
date: 2006-07-25
forum: General Help
---

### Post by daedalusman on 2006-07-25
I am getting this error when I try "make"ing the package...

```
tea_text_document.c:41:35: error: libgnomevfs/gnome-vfs.h: No such file or directory
tea_text_document.c:42:25: error: gconf/gconf.h: No such file or directory
tea_text_document.c:43:32: error: gconf/gconf-client.h: No such file or directory
tea_text_document.c:4252: error: syntax error before ‘*’ token
tea_text_document.c: In function ‘document_apply_hl’:
tea_text_document.c:4482: error: ‘GnomeVFSFileInfo’ undeclared (first use in this function)
tea_text_document.c:4482: error: (Each undeclared identifier is reported only once
tea_text_document.c:4482: error: for each function it appears in.)
tea_text_document.c:4482: error: ‘info’ undeclared (first use in this function)
tea_text_document.c:4483: error: ‘GnomeVFSResult’ undeclared (first use in this function)
tea_text_document.c:4483: error: syntax error before ‘r’
make[2]: *** [tea_text_document.o] Error 1
make[2]: Leaving directory `/home/aegon/tea-14.1.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/aegon/tea-14.1.0'
make: *** [all] Error 2
```

Does anyone have any idaes to help me out here, I tried installing the gnomevfs dev packages but that didn't change a thing? Thanks.

---

### Post by philippe_carlo on 2006-07-25
Try
```
sudo apt-get install libgconf2-dev libgnomevfs2-dev
```

You will probably run into more errors, concerning missing libraries. If you get errors like 

error: gconf/gconf.h: No such file or directory, then go to
[http://packages.ubuntu.org]("http://packages.ubuntu.org"), scroll all the way (Search the contents of packages) down and enter the missing file's name. You will get the package (usually ending on -dev) you need to install in order to compile the sources.

---

### Post by daedalusman on 2006-07-25
> **philippe_carlo said:**
> Try
```
sudo apt-get install libgconf2-dev libgnomevfs2-dev
```

You will probably run into more errors, concerning missing libraries. If you get errors like 

error: gconf/gconf.h: No such file or directory, then go to
[http://packages.ubuntu.org]("http://packages.ubuntu.org"), scroll all the way (Search the contents of packages) down and enter the missing file's name. You will get the package (usually ending on -dev) you need to install in order to compile the sources.

Nope, didn't work. And your link doesn't work, it gives "server not found" error, also I'm not really sure what you ment by that either. But thanks for the quick reply.

---

