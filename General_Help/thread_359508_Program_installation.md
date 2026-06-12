---
title: "Program installation?"
date: 2007-02-12
forum: General Help
---

### Post by smacd on 2007-02-12
I'm experienced with using Linux through school, however, I'm very new to actually setting up and managing a linux machine. I'm working on a project with another student, but I am having problems figuring out how to set some things up.

There are a number of programs that the project depends on, the major requirements listed are >=GTK 2.10.6, >=GSL 1.8, OpenCV 1.0, and the code thats already been written ([https://web.engr.oregonstate.edu/~hess/#%5B%5BSIFT%20Feature%20Detector%5D%5D)](https://web.engr.oregonstate.edu/~hess/#%5B%5BSIFT%20Feature%20Detector%5D%5D)).

I'm running Xubuntu 6.10. Someone told me to run the commands: "sudo apt-get update && sudo apt-get upgrade". and also "dpkg -l | grep gtk", and it appears I have GTK 2.10.6, and "dpkg -l | grep gsl" shows GSL 1.8-1.

I installed OpenCV (gunzipped, untarred, ./configure, make, sudo make install), and it appeared to install correctly. The problem comes when I attempt to run the make file on my partners code. The error I get reads as follows:

> gcc -03 -I../include `pkg-config --cflags opencv` `pkg-config --cflags gtk+-2.0` `pkg-config --cflags gsl` -c xform.c -o xform.o
Package gsl was not found in the pkg-config search path.
Perhaps you should add the directory containing `gsl.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gsl' found

I'm mainly using this as an example for the bigger problem I'm having... proper installation of programs. When I install a program, like GSL, how do I make sure that other programs know where it is? If I use apt-get to install a program like GSL, then where exactly IS it? Where do I find the gsl.pc file in order to add it to the pkg-config search path?

---

### Post by aysiu on 2007-02-12
I've moved your thread to a more appropriate place.

I'm not sure exactly what you're asking, but have you tried this? ```
sudo updatedb
locate gsl.pc
```

---

### Post by smacd on 2007-02-12
I just tried that, but it doesn't appear to be finding anything.

I guess I could clarify better. A program I am trying to install depends on another program that was installed using apt-get. But the program I am trying to install can't find the dependency, and I have no idea how to tell it where that program is.

---

### Post by Rui Pais on 2007-02-12
hi,
you need a solve a dependency for an app you want to compile. 
Those are always on -dev packages that you need to install with apt.

One potential good package would be: gsl-dev
but i always suggest, in those cases, to search [here]("http://packages.ubuntu.com/") for the specific file. I've got these:
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=gsl.pc&searchmode=searchfiles&case=insensitive&version=edgy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=gsl.pc&searchmode=searchfiles&case=insensitive&version=edgy&arch=i386)

so it seems you need:
```
sudo aptitude install libgsl0-dev
```


hth

---

