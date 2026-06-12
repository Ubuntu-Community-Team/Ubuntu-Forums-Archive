---
title: "GTK problem"
date: 2007-11-02
forum: General Help
---

### Post by ondrisko on 2007-11-02
Hello, I would appreciate very much some help with GTK.

I'd like to develop using GTK libraries, so I've installed package libgtk2.0-dev. I already solved problem with #include<gtk/gtk.h> which was not found at first, I added additional include directories to gcc.

Compilation works now ok, but there are linker errors like 'undefined reference to `gtk_init''. I cannot make him to find the libraries he wants and I dont know where to look for them.

Can anybody help please?

---

### Post by Thyme on 2007-11-02
Hi ondrisko,

Your include statement is fine :) I just use the following command when I compile my apps:

```

gcc -Wall -g <filename>**.c** -o <filename> `pkg-config --libs --cflags gtk+-2.0`

```

and the following which includes headers an libraries for mysql:

```

gcc -Wall -g -I/usr/include/mysql <filename>**.c** -o <filename> `pkg-config --libs --cflags gtk+-2.0` -L/usr/lib/mysql -lmysqlclient -lm

```

Let me know if this works or not ..

---

### Post by ondrisko on 2007-11-02
Works perfectly, thanks a lot!

...btw I know my include statement is fine, I just wanted to say that compiler couldnt find gtk.h at first. :D

---

### Post by Thyme on 2007-11-02
Cool man. Happy coding :)

---

