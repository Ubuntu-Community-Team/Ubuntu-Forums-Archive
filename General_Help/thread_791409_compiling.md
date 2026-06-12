---
title: "compiling"
date: 2008-05-12
forum: General Help
---

### Post by justborn on 2008-05-12
```
appy@appy-desktop:~/sphinx2$ ./configure – prefix=/usr
configure: WARNING: you should use --build, --host, --target
configure: WARNING: invalid host type: –
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for –-gcc... no
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

```

help me out

---

### Post by hermes0710 on 2008-05-12
```
sudo apt-get install build-essential
```

("make" is not installed)

---

### Post by justborn on 2008-05-12
i cannot get u

---

### Post by hermes0710 on 2008-05-12
You must install other packages in order to be able to compile. What you have to do is run a terminal (<alt>+F2 then type "gnome-terminal") and in the terminal type ```
sudo apt-get install build-essential
```

The error you get means that you miss the "make" package. Installing the build-essential package with the above command you won't have this problem

---

### Post by justborn on 2008-05-12
got it
but then dis
```
appy@appy-desktop:~/sphinx2$ ./configure &#8211; prefix=/usr
configure: WARNING: you should use --build, --host, --target
configure: WARNING: invalid host type: &#8211;
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for &#8211;-gcc... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for &#8211;-gcc... gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking whether byte ordering is bigendian... no
checking return type of signal handlers... void
[COLOR="Red"]checking build system type... Invalid configuration `&#8211;': machine `&#8211;' not recognized[/COLOR]

```

---

### Post by hermes0710 on 2008-05-12
Use "-prefix=/usr". You have a space between "-" and "prefix..."

---

### Post by justborn on 2008-05-12
```
appy@appy-desktop:~/sphinx2$ ./configure –prefix=/usr
configure: error: invalid variable name: –prefix

```

---

### Post by hermes0710 on 2008-05-12
./configure --prefix=/usr

---

### Post by Joeb454 on 2008-05-12
I thought it was```
--prefix=/usr
```

---

### Post by justborn on 2008-05-12
what should be the last line of the confi?

---

### Post by hermes0710 on 2008-05-12
What do you mean? Each configure has it's own structure

---

### Post by justborn on 2008-05-12
```
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GNOME_PANEL... configure: error: Package requirements (libpanelapplet-2.0 gtk+-2.0 libgnomeui-2.0 gstreamer-0.10 gstreamer-base-0.10 gdk-2.0 libwnck-1.0) were not met:

No package 'libpanelapplet-2.0' found
No package 'gtk+-2.0' found
No package 'libgnomeui-2.0' found
No package 'gstreamer-0.10' found
No package 'gstreamer-base-0.10' found
No package 'gdk-2.0' found
No package 'libwnck-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GNOME_PANEL_CFLAGS
and GNOME_PANEL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

---

### Post by justborn on 2008-05-12
from where do i get all the above dependencies

---

### Post by hermes0710 on 2008-05-12
Obviously you are missing some packages that the app you are trying to compile needs. Try installing them:

```

sudo apt-get install libpanelapplet gtk+ libgnomeui gstreamer gstreamer-base gdk libwnck

```

---

### Post by justborn on 2008-05-12
```
appy@appy-desktop:~/gnome-voice-control-0.1$ make dependencies
make: *** No rule to make target `dependencies'.  Stop.
appy@appy-desktop:~/gnome-voice-control-0.1$ sudo apt-get install libpanelapplet gtk+ libgnomeui gstreamer gstreamer-base gdk libwnck
Reading package lists... Done
Building dependency tree        
Reading state information... Done
E: Couldn't find package libpanelapplet
```

---

### Post by hermes0710 on 2008-05-12
See all the dependencies and try installing them one by one (in the previous post i removed the version numbers from the names but it seems they are needed, you can't know the package names, you have to search). For the first one it might be libpanelapplet-2.0.

---

### Post by justborn on 2008-05-12
can u give me best links to each of the dependencies.

---

### Post by hermes0710 on 2008-05-12
Follow this url and search via the dependencies as keywords to find the packages you need:

[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

---

### Post by justborn on 2008-05-12
it doest not have it

---

### Post by hermes0710 on 2008-05-12
What are you trying to install? Which application?

---

### Post by justborn on 2008-05-12
gnome voice control-1.0

---

### Post by ad_267 on 2008-05-12
Go to system - administration - synaptic package manager and search for these. You will also need any that have the "-dev" suffix for compiling software.

Edit: Gnome-voice-control is available from the repositories. Just search for it in synaptic.

---

### Post by justborn on 2008-05-12
i cannot get u

---

### Post by ad_267 on 2008-05-12
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by syanideatresillience on 2012-05-03
your problem is that you've only got one dash.  It should be two:
./configure --prefix=/usr

---

### Post by oldos2er on 2012-05-03
Old thread closed. Please don't bump old threads.

---

