---
title: "pkg-config errors when installing software"
date: 2007-03-12
forum: General Help
---

### Post by nnp on 2007-03-12
Hi, when trying to install two different pieces of software over the past two days i've been met with a similar error when using their ./configure script. Something similar to the following 

> 
checking for EKIGA... configure: error: Package requirements (gtk+-2.0 >= 2.6.0 gthread-2.0 >= 2.4.0 esound >= 0.2.28 gconf-2.0 >= 2.2.0 libgnome-2.0 >= 2.2.0 libgnomeui-2.0 >= 2.2.0) were not met:

No package 'gtk+-2.0' found
No package 'gthread-2.0' found
No package 'esound' found
No package 'gconf-2.0' found
No package 'libgnome-2.0' found
No package 'libgnomeui-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables EKIGA_CFLAGS
and EKIGA_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.



and 

> 
checking for qt-mt >= 3.3.0 qt-mt < 4.0... Package qt-mt was not found in the pkg-config search path. Perhaps you should add the directory containing `qt-mt.pc' to the PKG_CONFIG_PATH environment variable No package 'qt-mt' found Package qt-mt was not found in the pkg-config search path. Perhaps you should add the directory containing `qt-mt.pc' to the PKG_CONFIG_PATH environment variable No package 'qt-mt' found
configure: error: Library requirements (qt-mt >= 3.3.0 qt-mt < 4.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.



In both cases all the above software is installed but there doesnt seem to be any .pc entries, for example 

> 
nnp@ubuntu1:~/sipphones/twinkle-1.0$ find / -iname "qt-mt*.pc" 2>/dev/null
nnp@ubuntu1:~/sipphones/twinkle-1.0$ find / -iname "gtk*.pc" 2>/dev/null
/usr/lib/pkgconfig/gtk-dotnet-2.0.pc
/usr/lib/pkgconfig/gtk-sharp-2.0.pc
/usr/lib/pkgconfig/gtkhtml-sharp-2.0.pc
nnp@ubuntu1:~/sipphones/twinkle-1.0$ find / -iname "gconf*.pc" 2>/dev/null
/usr/lib/pkgconfig/gconf-sharp-2.0.pc


Anyone have a solution for this or a work around?

Thanks,
NNP

---

### Post by BlueEagle on 2007-05-06
When compiling from source you need to make sure that the development packages (packagename-dev) for the libs needed (in your case GTK and friends) are installed.

This is because the header files for the libs aren't installed by the default packages.

Hope that helps.

---

