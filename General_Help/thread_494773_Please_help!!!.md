---
title: "Please help!!!"
date: 2007-07-07
forum: General Help
---

### Post by deathspell on 2007-07-07
I followed the instructions on installing dc++ from another post in this forum...


I get the following error when I type sudo scons
```

scons: Reading SConscript files ...
Checking for g++ >= 3.4...(cached) yes
Checking for pkg-config... yes
Checking for gtk+-2.0 >= 2.6... no
        gtk+ >= 2.6 not found.
        Note: You might have the lib but not the headers
```

I downloaded gtk+-2.8.0.tar.bz2 and tried to install it and it said it needed glib-2.12.9.tar.bz2 and pango-1.16.4.tar.bz2 (I chose the latest versions in the list...)


while installing glib, it said I needed gettext.. so I installed that too... 

What do I do now? I have gtk+-2.8.0.tar.bz2 .. after I extract it and go into the folder to type "make" after configure.. it says ```
make: *** No targets specified and no makefile found.  Stop.
```

So I'm stuck here.. Please help me! I'm completely clueless.. am I still missing files? What to do next? :(:(:(:(:(:(:(:(

---

### Post by deathspell on 2007-07-07
When I configure, I get this

```
configure: error: Package requirements (glib-2.0 >= 2.7.1    atk >= 1.0.1    pango >= 1.9.0    cairo >= 0.9.2) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the BASE_DEPENDENCIES_CFLAGS and BASE_DEPENDENCIES_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.

```

I installed all those already :S

---

### Post by deathspell on 2007-07-07
Maybe I didn't install the right versions? How do I remove the incorrect ones now?

---

### Post by cactaur on 2007-07-07
Woah woah, hold up there. Now, first we'll fix your first problem. To install gtk+2.0, you just need the libgtk2.0-dev package, which is available from the repositories. If you do that, you won't be caught in what is called dependency hell.

```
sudo apt-get install libgtk2.0-dev
```

Now, to uninstall the packages you compiled. Installing from source is quite messy, and it's not guaranteed you'll be able to uninstall everything. That's why you want to install from the repositories whenever possible. Now, the way to uninstall those is to go back to the original source directory, the directory created after you unpacked the tar, then typing "sudo make uninstall". Now, this isn't guaranteed, but it might work.

To make removal of source packages easier from now on, you can also install "checkinstall"

```
sudo apt-get install checkinstall
```

Now, instead of typing "sudo make install", just type "sudo checkinstall". With checkinstall, you can just uninstall by going into Synaptic and uninstall it like a regular package.

Oh, and one more thing. Use something more specific as a title for your thread. Most people look over "Please help". I hope this post will help you.

---

