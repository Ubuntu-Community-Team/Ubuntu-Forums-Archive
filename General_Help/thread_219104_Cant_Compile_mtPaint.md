---
title: "Cant Compile mtPaint"
date: 2006-07-19
forum: General Help
---

### Post by BuffaloX on 2006-07-19
When I try to Compile MTpaint
[http://mtpaint.sourceforge.net/]("http://mtpaint.sourceforge.net/")

which seems to be really simple
I get this error...

[I]bill@logic1:~/Desktop/mtpaint$ make
make -C src
make[1]: Entering directory `/home/bill/Desktop/mtpaint/src'
gcc -Wall -O2  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include  -DVERSION="\"mtPaint 3.01"\"   -c -o main.o main.c
/bin/sh: gcc: command not found
make[1]: *** [main.o] Error 127
make[1]: Leaving directory `/home/bill/Desktop/mtpaint/src'
make: *** [src] Error 2
[/I]

Please help.

---

### Post by mlind on 2006-07-19
You'll have to install package called build-essential
```

sudo aptitude install build-essential

```

---

### Post by BuffaloX on 2006-07-19
Thanx now it starts compiling. :p 
But I seem to need some library. I get this error:

main.c:24:24: error: gdk_imlib.h: No such file or directory
In file included from main.c:28:
memory.h:20:17: error: png.h: No such file or directory
In file included from main.c:28:

And a hole lot of errors that seem to be a result thereof.

---

### Post by mlind on 2006-07-19
> **BuffaloX said:**
> Thanx now it starts compiling. :p 
But I seem to need some library. I get this error:

main.c:24:24: error: gdk_imlib.h: No such file or directory
In file included from main.c:28:
memory.h:20:17: error: png.h: No such file or directory
In file included from main.c:28:

And a hole lot of errors that seem to be a result thereof.

Install package called **apt-file** which you can use to query the packages you need to install to get necessary files. When compiling, you usually want to install packages that have **-dev** suffix.
Packages you want are gdk-imlib11-dev and libpng12-dev.
```

sudo aptitude install gdk-imlib11-dev libpng12-dev

```


You can also use debian search to locate package contents online
[http://www.debian.org/distrib/packages#search_contents](http://www.debian.org/distrib/packages#search_contents)

---

### Post by BuffaloX on 2006-07-19
GREAT! **mlind** it works now, Nice app too. :p 

I also tried apt-file, but I couldn't figure out how it worked off-hand.

I tried:
 apt-file search gdk_imlib.h
I got nothing...

I then tried the link to debian packages.
got this result:
oldlibs/gdk-imlib1-dev

Which I guess would have been good enough to find the newer version. :p 

Once again thanx mlind you even gave me more help than I aasked for. :-D

---

### Post by mlind on 2006-07-19
apt-file uses its own database, which you need to 'update', like you're doing with aptitude or apt-get.
```

sudo apt-file update

```

Then search using
```

apt-file search png.h

```

---

### Post by BuffaloX on 2006-07-19
> **mlind said:**
> apt-file uses its own database, which you need to 'update', like you're doing with aptitude or apt-get.


Great, that's a very cool tool to have, :p 
I thought the database would have been included with the install, but it's nice to now know how to update it. 

the list of the search result was initially i bit long
I reduced it some by using:

apt-file -l -F search png.h

I'm very proud I figured *( -l -F )* out all by myself.  :-\"

---

