---
title: "Setting CGG optimization flags"
date: 2005-10-19
forum: General Help
---

### Post by Skrewdriver on 2005-10-19
I've got an IBM T21 Thinkpad, and I've been trawling around the [http://www.thinkwiki.org]("http://www.thinkwiki.org") site (Linux for Thinkpads). One of the things I came across is a set of flags for GCC optimization for the Pentium Mobile III. 
```
-Os -march=pentium3 -fomit-frame-pointer -pipe
```

I'm fairly inexperienced at compiling from source (one successful attempt so far) and I would like to set these flags but I don't know where (ie what file) when or how to set them.

Can someone please point me in the right direction?

Thanks
Mark

---

### Post by Miguel on 2005-10-19
If you are not running short of space, try using -O2 instead of -Os. The difference between both is that -Os does not use optimizations that increase binary size.

Other than that, It could be useful to try -mfpmath=sse

Anyway, I'm neither an expert nor a Gentoo Stage 1 user so...

BTW: Some guys swear for -O3 optimizations. The problem with these is it doesn't always improve from -O2. If you'r desperately looking for performance, try this... but it might not work

2nd BTW: I also have a laptop (centrino based), and the biggest performance improvement for me would be... a faster HD.

---

### Post by Skrewdriver on 2005-10-19
Thanks Miguel for the pointers (and fast reply), but it still doesn't answer my question ... when (or where) do I set these flags? Should I edit a config file somewhere, or when I am doing make/make install or something like that.

Thanks mate
Mark

---

### Post by Miguel on 2005-10-19
Oh sorry!

There are two ways. You can specify them while configuring:
```

./configure CFLAGS="-O2 -march=pentium3 -mfpmath=sse -fomit-frame-pointer -pipe"

```

Where you can put valid options between the "". However, check your documentation, because you could have another name for CFLAGS (even though this is the default). For example, FORTRAN77 flags could be G77FLAGS or FFLAGS or F77FLAGS (depending on the software)

Or you could do the ./configure and then manually edit the make.sys file created. You could here look for a line begining (or similar) with CFLAGS= and add here the flags you want (always between ")

There is also a third option (a bit more subtle). You can also set your compilation flags as an environment variable. How can you do that? you could type in a terminal
```

CFLAGS="-O2 -march=pentiumiii"
export CFLAGS

```
This is valid until you change and reexport CFLAGS or  you close your current terminal. You can always check it with
```

echo $CFLAGS

```

If you are not familiar with these commands, I will explain them a bit in a furhter post.

Hope it helps,

Miguel

---

### Post by Skrewdriver on 2005-10-19
That's brillant, thanks Miguel.

I think I will go with the environment variable option. Is there somewhere I can set it permanently so I don't lose it when I close the terminal?

Thanks again
Mark

---

### Post by Miguel on 2005-10-19
You could edit ~/.bashrc so this has permanent settings. Just open .bahsrc with the editor you most hate and add to the bottom of the file
```

CFLAGS="-O2 -whateveryouwant" 
export CFLAGS

```

These changes will make effect as soon as you run
```

. ~/.bashrc

```

The space between the "." and the "~" is important. Do an echo $CFLAGS to test it (also from a  new terminal).

But BEWARE!!! These options will be ALWAYS loaded whether you want it or no. Just remember to change those flags in case you want to compile something more specific, such as a kernel. 

Of course, these changes can always be restored by commenting the previous lines (or deleting them altogether) and running
```

. ~/.bashrc

```

Hope it helps,

Miguel

PS: If you are using tcsh or csh as your shell, the export command will not work. The equivalent in this case is the "setenv" command. Ubuntu uses bash 3.0 by default. If you want to check your current shell, just type "echo $SHELL"

PS2: Note that, in order to compile programs, you will need the development part of libaries. These are named the same as the normal libraries, but end with "-dev". These are, of course, also available with synaptic.

---

### Post by doclivingston on 2005-10-19
[QUOTE=Miguel]BTW: Some guys swear for -O3 optimizations. The problem with these is it doesn't always improve from -O2. If you'r desperately looking for performance, try this... but it might not work[/QUOTE]

And -O3 can also completely break applications, causing them to crash. Some work, some don't - if you get a crash in an application that you compiled at -O3, try it without that before filing a bug.

---

