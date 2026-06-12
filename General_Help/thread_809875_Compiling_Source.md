---
title: "Compiling Source"
date: 2008-05-27
forum: General Help
---

### Post by amtur_poet on 2008-05-27
I can't figure out how to compile source code. I downloaded the build-essential package from synaptic and installed it, but whenever I go to a folder with the source code and use the ./configure command, it says that there is no such file or directory. I know that's not true, because I can see it right in the folder. The file I'm trying to compile is here: [http://archive.ubuntu.com/ubuntu/pool/universe/c/compiz-fusion-plugins-unsupported/compiz-fusion-plugins-unsupported_0.6.0-2.dsc](http://archive.ubuntu.com/ubuntu/pool/universe/c/compiz-fusion-plugins-unsupported/compiz-fusion-plugins-unsupported_0.6.0-2.dsc)

Can someone help me?

---

### Post by logos34 on 2008-05-27
Isn't there a .deb pkg somewhere?

If not, then you need to use the *.orig.tar.gz file

Assuming you're using Hardy:
[http://packages.ubuntu.com/source/hardy/x11/compiz-fusion-plugins-unsupported](http://packages.ubuntu.com/source/hardy/x11/compiz-fusion-plugins-unsupported)
(bottom)

---

### Post by haggus on 2008-05-27
try sudo ./configure

---

### Post by amtur_poet on 2008-05-27
I have a more serious problem with compiling. I've tried this on Feisty, Gutsy, and now Hardy, but with no luck: when I run the "sudo make" command, it always, no matter what the package, says "make: *** No targets specified and no makefile found.  Stop." I've tried it with about 20 different packages, and none worked when I ran make.

---

### Post by amtur_poet on 2008-05-27
> Isn't there a .deb pkg somewhere?
If there is, could someone give me a link?

---

### Post by logos34 on 2008-05-27
> **amtur_poet said:**
> I have a more serious problem with compiling. I've tried this on Feisty, Gutsy, and now Hardy, but with no luck: when I run the "sudo make" command, it always, no matter what the package, says "make: *** No targets specified and no makefile found.  Stop." I've tried it with about 20 different packages, and none worked when I ran make.

you must have been using the wrong ones

the usual command sequence is:

cd /parent/directory

./configure
make
sudo make install

---

### Post by amtur_poet on 2008-05-27
That's what I've been trying. Does anyone have a .deb link? That would be very helpful.

---

### Post by amtur_poet on 2008-06-06
I've never been able to compile anything on my system. Are there any extra packages I need to install through synaptic first, besides build-essential, which doesn't work?

---

### Post by Joeb454 on 2008-06-06
You need to install the dependencies of the application. Sometimes you can do ```
sudo apt-get build-dep <packagename>
``` to get them - or you could do it the way I do

```
./configure
```see what errors the configure returns about dependencies - install that dependency :)

---

### Post by amtur_poet on 2008-06-06
```
sudo apt-get build-dep build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by 3rdalbum on 2008-06-06
Are you sure your terminal is in the same directory as the "configure" file? Install the "nautilus-open-terminal" package, log out and then log in again. You'll be able to right-click inside any Nautilus window and choose "Open Terminal Here", to make sure you're definitely in the correct folder.

Also, check that the "configure" script has execute permission for your user account.

The build-essential package brings in the basic programs and libraries for compiling. You will usually also need development headers for the libraries that are being used by the program itself. For instance, if you're compiling a music playing program, it might give you an error message that you are missing Gstreamer. You'd go to Synaptic and search for all packages with "gstreamer" and "-dev" in their names, install them, and try the configure step again. Packages that end with "-dev" are development headers; the things that the compiler needs to compile against.

It sounds complicated at first, but once you understand what's going on, it'll be much easier.

---

### Post by 3rdalbum on 2008-06-06
> **amtur_poet said:**
> ```
sudo apt-get build-dep build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

No, the package name should be the name of the package that you're trying to compile. For instance, if you were compiling a new version of Gnash, you'd do:

```
sudo apt-get build-dep gnash
```

Only works for programs that have versions in the repositories, of course.

---

### Post by TSUs on 2008-06-06
I have this problem too. I did try several times before, and I did use Google, but I don't know how to compile.

./configure, make and I get this: 

make: *** No targets specified and no makefile found. Stop.


[http://www.nongnu.org/gcmd/index.html](http://www.nongnu.org/gcmd/index.html)

There are no errors as I can see, but for some reason it does not work. :(

*.deb?

---

