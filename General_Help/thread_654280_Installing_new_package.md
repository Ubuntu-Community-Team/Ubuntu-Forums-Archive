---
title: "Installing new package"
date: 2007-12-30
forum: General Help
---

### Post by awilki01 on 2007-12-30
I'm trying to install a package named "gkrellm" to monitor my CPU temp, etc.  It requires the GTK+ package.  I tried installing that package, but it required other packages?  Can it really get any more difficult?

In any event, I downloaded all the TAR files for the packages needed for GTK+.  One of them was GLIB.  When doing the "./configure" for one of the packages required for GTK+, it indicates below it needs GLIB as well - which I did successfully make, etc. However, I am getting the following error.


> checking for GLIB - version >= 2.5.7... 
*** 'pkg-config --modversion glib-2.0' returned 2.12.13, but GLIB (2.14.1)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLIB 2.5.7 or better is required. The latest version of
*** GLIB is always available from [ftp://ftp.gtk.org/](ftp://ftp.gtk.org/). If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.

It's telling me things to do, but I just don't understand exactly.  Any help would be greatly appreciated?

Also, none of these packages show up in Synaptic.  Shouldn't atleast GLIB show up after it is installed?

And, are all packages this difficult to install???  I feel this is borderline insanity.  I know it stems from lack of experience with Linux, but this is really not making it very newb friendly.

---

### Post by jken146 on 2007-12-30
Go to System > Administration > Software Sources and make sure that all the repositories are enabled.

Then you can install gkrellm (it's in the universe repo):  ```
sudo aptitude install gkrellm
```

All dependencies will be handled for you -- this is all you need to do.

If you want a simple reference on installing things in Ubuntu, try this:  [http://monkeyblog.org/ubuntu/installing](http://monkeyblog.org/ubuntu/installing)

---

### Post by weldan on 2007-12-30
seems like the gkrellm package already have at repo. you can install it with apt-tools than install it from scratch. installing packages from scratch is good, if you know what to do. :KS

---

### Post by awilki01 on 2007-12-31
WOW!!!!  That was easy!!!

I guess it will take some experience with Linux before I know what I'm doing.

Thanks again to both of you!

---

