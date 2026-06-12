---
title: "Trying to install a program from source (ggobi/rggobi)"
date: 2006-09-07
forum: General Help
---

### Post by roncrump on 2006-09-07
Hi,

I saw someone playing with the data visualisation software ggobi at work, and was very impressed and decided to install it myself.

It appeared that the version in the multiverse repository was quite a bit behind that available from ggobi.org, so I downloaded the source tar file and followed the instructions.

I didn't get very far. Running the configure script I got the following error:

> checking for GTK... configure: error: Package requirements (gtk+-2.0 >= 2.6.0) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Now, I'm pretty much positive that GTK is on the machine, so does anyone have a suggestion what to do? I can't find any *gtk*.pc files, so don't think there is anything for pkg-config to work with for gtk (may be wrong, may be looking for the wrong thing).

There is a package available from the debian site: can I just grab this and run with it? Will it detect all required dependencies as you would expect a ubuntu package to?

When I have installed, either from source or the debian package, will this mess up future ubuntu upgrades: will it be detected as installed, and if so will it attempt to downgrade it to the ubuntu repository version (or upgrade it automatically if ubuntu ends up with a newer version than I have?).

Thanks.

Ron.

---

### Post by croak77 on 2006-09-07
Do you have libgtk2.0-dev installed?

---

### Post by amo-ej1 on 2006-09-07
Indeed, there are typically two versions of library. A package containing the  actually dynamic loadable library, which any user of an application will want to have installed. And a development version (packagename suffixed by -dev) this packages contains the headers and additional documentation that developers (or people that compile their own applications) will need to have in order to be able to link agains the given library. 

```

user@lap:~$ apt-cache search libgtk2.0
libgtk2.0-cil - CLI binding for the GTK+ toolkit 2.8
libgtk2.0-0 - The GTK+ graphical user interface library
libgtk2.0-0-dbg - The GTK+ libraries and debugging symbols
libgtk2.0-bin - The programs for the GTK+ graphical user interface library
libgtk2.0-common - Common files for the GTK+ graphical user interface library
libgtk2.0-dev - Development files for the GTK+ library
libgtk2.0-doc - Documentation for the GTK+ graphical user interface library

```
So installing libgtk2.0-dev should solve your issue, and now you'll be ready to encounter another one :p

---

### Post by roncrump on 2006-09-10
Thanks. That fixed it.

---

