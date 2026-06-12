---
title: "(newb) PKG_CONFIG_PATH?"
date: 2005-07-09
forum: General Help
---

### Post by Flakes on 2005-07-09
sorry for all these newbie questions, but im trying to install lincity-ng and i come up with this error 
[COLOR=Red]
checking for libxml-2.0 >= 2.6.11... Package libxml-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxml-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxml-2.0' found

configure: error: Library requirements (libxml-2.0 >= 2.6.11) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.[/COLOR]

now i know that it isn't called libxml-2.0.pc on ubuntu, its libxml2 right? where do i go to modify this (also please correct me if i'm wrong)

---

### Post by Dogmeat on 2005-07-09
You need libxml2-dev:

```
sudo apt-get install libxml2-dev
```

Also, you may need other libraries so check the README or INSTALL file to find out which ones.

If it gives you an error on a specific file, you can search which package it belongs to [here](http://packages.ubuntu.com/)!   :)

---

### Post by Flakes on 2005-07-09
thanks for the link! :)

---

### Post by Flakes on 2005-07-09
after installing the package you reccommended, i end up with the same error...?

---

### Post by Dogmeat on 2005-07-10
Thats odd.. do you have pkg-config installed? 
Type this in a terminal:

```
echo $PKG_CONFIG_PATH
``` 

You should get something like ```
/usr/local/lib/pkgconfig:/usr/lib/pkgconfig
```  

If not, apt-get pkg-config! Then try it again, you should see that line. Recompile and it should work!

By the way don't remove libxml2-dev.. you will still need it

---

### Post by Flakes on 2005-07-10
[QUOTE=Dogmeat]Thats odd.. do you have pkg-config installed? 
Type this in a terminal:

```
echo $PKG_CONFIG_PATH
``` 

You should get something like ```
/usr/local/lib/pkgconfig:/usr/lib/pkgconfig
```  

If not, apt-get pkg-config! Then try it again, you should see that line. Recompile and it should work!

By the way don't remove libxml2-dev.. you will still need it[/QUOTE]
 i typed echo $PKG_CONFIG_PATH and get a blank space... and then i try to sudo apt-get install pkg-config, and it says i have the latest version! grr... i dont know whats wrong

---

### Post by Dogmeat on 2005-07-10
put this line at the end of .bashrc in your home folder;

```

PKG_CONFIG_PATH=/usr/local/lib/pkgconfig:/usr/lib/pkgconfig
```

---

### Post by baytuni on 2006-11-02
I have a similar problem too. When I try to install gaim-rythmbox this error message comes. 
```
checking for gaim... configure: error: Package requirements (gaim >= 2.0.0) were not met:

No package 'gaim' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables gaim_CFLAGS
and gaim_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

and what is PKG_CONFIG anyway?

---

