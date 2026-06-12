---
title: "Is it possible to run make install from another directory?"
date: 2015-04-06
forum: General Help
---

### Post by Alex_Baggott on 2015-04-06
Hi all.  I know that ```
make install
``` is run from inside the directory which contains the makefile. Is it possible to run make install on this directory from outside of it?

---

### Post by sisco311 on 2015-04-06
Why?

---

### Post by steeldriver on 2015-04-06
You could use the -C flag, I think

```

       -C dir, --directory=dir
            Change to directory dir before reading the makefiles or doing any&#8208;
            thing else.  If multiple -C options are specified, each is  inter&#8208;
            preted  relative to the previous one: -C / -C etc is equivalent to
            -C /etc.  This is typically used  with  recursive  invocations  of
            make.


```

i.e.

```

make -C path/to/dir/containing/makefile install

```
e.g.
```

$ make -C forums/src/ hello
make: Entering directory `/home/steeldriver/Documents/forums/src'
g++ -Wall -g -o hello hello.cpp

```

---

### Post by Alex_Baggott on 2015-04-08
Thanks. That worked beautifully.

For any others wondering about  this, it also works with "make install", i.e.:
```
make install -C  <directory_name>
```

---

