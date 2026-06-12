---
title: "meanwhile installation problems"
date: 2005-06-08
forum: General Help
---

### Post by José Serra on 2005-06-08
Hello everybody, I'm having problems with the meanwhile installation.

first I've downloaded meanwhile-0.3.tar.gz
but when I try execute **./configure --prefix=/usr**
I got this error:

checking for GLIB - version >= 2.0.0... no
[I]*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error:
*** GLib 2.0 is required.[/I]

when I execute: **pkg-config --modversion glib**

[I]sh: glib-config: command not found
sh: glib-config: command not found
sh: glib-config: command not found[/I]

what can I do?

Thanks

---

### Post by shakin on 2005-06-08
```

$ sudo apt-get install libglib2.0-dev

```

---

### Post by José Serra on 2005-06-08
I execute  **sudo apt-get install libglib2.0-dev**
[I]
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
E: No se pudo encontrar el paquete libglib2.0-dev[/I]

As you can see my system it's in Spanish... apt-get can't find the package.

---

### Post by José Serra on 2005-06-08
Ok... someone else told me about my error.

in Ubuntu Forums > Ubuntu Hoary Hedgehog 5.04  > Hoary 5.04 Application Support  > Installation Help >  Can't find some packages.

...I hope to come back with better questions ;-) 

See you.

---

