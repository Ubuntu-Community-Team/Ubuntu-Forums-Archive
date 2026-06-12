---
title: "missing &quot;configure&quot; bash script"
date: 2013-05-02
forum: General Help
---

### Post by kedmond on 2013-05-02
I am using Ubuntu 12.04.  Somehow my install is missing the "configure" bash script.  How do I go about installing this?  Thanks.

---

### Post by MG&amp;TL on 2013-05-02
There isn't one. If you're referring to the './configure, make, make install' way of installing programs, that isn't necessarily how they come any more (despite certain persons' advice to the contrary). You'll have to tell us what software you're trying to install if you want help with it. :)

---

### Post by kedmond on 2013-05-02
> **MG&TL said:**
> There isn't one. If you're referring to the './configure, make, make install' way of installing programs, that isn't necessarily how they come any more (despite certain persons' advice to the contrary). You'll have to tell us what software you're trying to install if you want help with it. :)

Yes, ./configure is what I was referring to.

The program I am trying to compile and install is the Pixie Renderer.  Information about installation on UNIX is here: [http://www.renderpixie.com/pixiewiki/Documentation/Installing_And_Running#UNIX](http://www.renderpixie.com/pixiewiki/Documentation/Installing_And_Running#UNIX)

I remember that a few years ago there was a .deb package for Pixie...but I can no longer find it.

Thanks for the help.

---

### Post by MG&amp;TL on 2013-05-02
According to the page, > You can download the Pixie source code as a tgz file. so do that. Then extract the file you downloaded into a convenient directory (I'll assume 'Documents/pixie' from now on).

Then open a terminal. Type (in order):

```
[FONT=arial]cd ~/Documents/pixie/
./configure --prefix=/usr/local/Pixie --enable-selfcontained
make
sudo make install[/FONT]
```

---

### Post by kedmond on 2013-05-02
> **MG&TL said:**
> According to the page,  so do that. Then extract the file you downloaded into a convenient directory (I'll assume 'Documents/pixie' from now on).

Then open a terminal. Type (in order):

```
[FONT=arial]cd ~/Documents/pixie/
./configure --prefix=/usr/local/Pixie --enable-selfcontained
make
sudo make install[/FONT]
```

Wow, you must think I'm really stupid.

See the command that you copy-pasted for me?  It has a "./configure" bash script command.  I don't have that on my computer.  And you just said earlier today that Ubuntu no longer uses that method.

---

### Post by MG&amp;TL on 2013-05-02
> **kedmond said:**
> Wow, you must think I'm really stupid.

See the command that you copy-pasted for me?  It has a "./configure" bash script command.  I don't have that on my computer.  And you just said earlier today that Ubuntu no longer uses that method.

Not stupid! There's just a lot of misconceptions about this, I like to make it simple. :)

How a project compiles itself is entirely up to its authors. For quite a while, the most popular way of doing this was a system called GNU Autotools. (this uses './configure' to configure the project, and is the origin of the famous './configure, make make install' triplet.). Nowadays, other build systems such as CMake, SCons, and others are more prevalent, but Autotools is still very popular. So 'not necessarily' is what I said. Now that I know the project uses Autotools, we can proceed.

Now, to your problem. You say that 'I don't have the configure script on your computer'. './configure' is *not* something you have to install: it's an executable file (it's a bash script) shipped with the project. ('./' means look in the current directory for executables). What error message do you get when you try to run that command?

---

### Post by steeldriver on 2013-05-02
Are you sure you got the correct archive? I just grabbed the one from the sourceforge project page

[http://sourceforge.net/projects/pixie/files/pixie/Pixie%202.2.6/Pixie-src-2.2.6.tgz/download](http://sourceforge.net/projects/pixie/files/pixie/Pixie%202.2.6/Pixie-src-2.2.6.tgz/download)

and it configured OK for me [**NB there is a 2.2-6 deb file for i386 there as well - may save you the trouble of building**]

AFAIK there is no single "./configure" bash script command that you would "have on your computer" - each source package that uses autoconf provides its own configure script (hence why it's invoked as **./**configure)


EDIT: there's also a git repository that may be more recent (the latest tarball on sourceforge is 2009) - however that appears to use CMake not autoconf

---

### Post by kedmond on 2013-05-03
That .deb file worked.  Thank you!  And thanks for the explaining the "configure" script.  The archive that I downloaded didn't come with one.  How would I use CMake, since that's what the git version comes with.  Thanks again.

---

### Post by oldos2er on 2013-05-03
Nearly every time I've used cmake to compile something, instructions on how to do so are included in a README or INSTALL file that accompanies the code.

---

