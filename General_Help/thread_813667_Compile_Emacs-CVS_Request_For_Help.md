---
title: "Compile Emacs-CVS: Request For Help"
date: 2008-05-31
forum: General Help
---

### Post by geeree on 2008-05-31
While installing an application via confiure-make-make install, how do I help configure see library files present at non-standard locations?

I want to compile the CVS version (23.0.60.1) of GNU Emacs on an OpenSUSE 10.2 machine that I don't have root access to. I am interested in font rendering support for the Devanagari script. Emacs requires the otf and m17n-flt libraries for that.

Since I do not have root access to my system, I installed these libraries in $HOME/lib. (The header files went into $HOME/include.) But while compiling Emacs, I found that configure does not detect these libraries, I have tried the following:

[LIST=1]
[*]export LD_LIBRARY_PATH=$HOME/lib
[*]LDFLAGS='-L$HOME/lib' CPPFLAGS='-I$HOME/include' ./configure --enable-font-backend --prefix=$HOME --with-otf --with-m17n-flt
[*]./configure --enable-font-backend --prefix=$HOME --with-otf --with-m17n-flt --libdir=$HOME/lib
[/LIST]

How can I make configure see these library files?

Thanks,
Girish.

---

### Post by HalPomeranz on 2008-05-31
Set CFLAGS and LDFLAGS as environment variables and then run configure:

```

export CFLAGS=-I$HOME/include
export LDFLAGS=-I$HOME/lib
./configure --enable-font-backend --prefix=$HOME --with-otf --with-m17n-flt

```

I don't believe you'll need the --libdir=$HOME/lib option on the configure command line, since that should be implied by your --prefix option.

---

### Post by geeree on 2008-05-31
> **HalPomeranz said:**
> Set CFLAGS and LDFLAGS as environment variables and then run configure:

Thanks for the reply. I tried this. But it didn't work. configure still couldn't find the libotf and m17n-flt libraries, although they are clearly in $HOME/lib and $HOME/include. Here are the relevant lines from config.log: 

```

configure:13205: checking for pkg-config
configure:13236: result: /usr/bin/pkg-config
configure:13250: checking for libotf
configure:13270: result: no
configure:13311: checking for pkg-config
configure:13342: result: /usr/bin/pkg-config
configure:13356: checking for m17n-flt
configure:13376: result: no

```

It says configure cannot find libotf or m17n-flt. Any idea?

---

### Post by HalPomeranz on 2008-05-31
Ah, it's using pkg-config to find the libraries.  You need to set your PKG_CONFIG_PATH environment variable so that it contains the directories that hold the *.pc files for the libraries you installed.  In your case, this is probably $HOME/lib/pkgconfig, so you would set:

```

export PKG_CONFIG_PATH /usr/lib/pkgconfig:/usr/local/lib/pkgconfig:$HOME/lib/pkgconfig

```

Then run the configure command.

---

### Post by geeree on 2008-05-31
> **HalPomeranz said:**
> Ah, it's using pkg-config to find the libraries.  You need to set your PKG_CONFIG_PATH environment variable so that it contains the directories that hold the *.pc files for the libraries you installed. 

Yep! That works. Unfortunately though, something goes wrong while compiling. I get an error message: 

```

src/temacs: error while loading shared libraries: libotf.so.0: cannot open shared object file: No such file or directory

```

Evidently, the compiler cannot find libotf.so.0, which actually is present in $HOME/lib. I tried pointing this directory out by exporting LDFLAGS suitably. But that didn't work. Maybe I'll have to look at it later again. 

But thanks for your help.

---

### Post by HalPomeranz on 2008-05-31
That error message is occurring when the build is trying to execute the temacs program.  It looks like you also need to set your LD_LIBRARY_PATH:

```

export LD_LIBRARY_PATH=/lib:/usr/lib:/usr/local/lib:$HOME/lib

```

Note that you will need to make this LD_LIBRARY_PATH setting any time you want to run a program that uses the libraries you have installed in your homedir, so I suggest you add the above setting to your .bashrc (or some other start up file that gets run when you log in).

---

