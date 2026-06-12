---
title: "Package gtk+-2.0 was not found"
date: 2007-03-04
forum: General Help
---

### Post by Boni2k on 2007-03-04
Hello,
I try to compile a program but I get the message
[i]checking for gtk+-2.0 >= 2.0.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.[/i]

Anyhow, I have libgtk2.0-dev and all the rest installed. So why is that? How to fix?

Greets, Jonas

---

### Post by Boni2k on 2007-03-06
Help is appreciated...

---

### Post by Malakia on 2007-03-06
For one thing sometimes it takes a while for people to answer so calm down. Find out where the gtk package installed to and then put that path in the terminal like this

```
 ./configure /path to gtk 
```

---

### Post by Boni2k on 2007-03-06
Did not work, the Configure script is unusual:

if ! pkg-config  --print-errors --exists 'gtk+-2.0 >= 2.6.0'; then
    echo 'Please install (or upgrade to) GTK+ 2.6.0, at least.'
    exit 1
fi

I uncommented these lines but compiling didnt work saying GTK Error, I really wonder what that is

---

### Post by Boni2k on 2007-03-11
Problem still exists...

---

### Post by nick_jensen on 2007-05-05
EDIT

I don't know what your problem is.

---

### Post by sdide on 2007-05-05
Where is your gtk+-2,0.pc located?

~# dpkg-query -S gtk+-2.0

---

### Post by blakdogg on 2007-05-31
I would suggest using synaptic and a search of libgtk to verify the packages are there. I had a similar problem (didn't check the messages for exact match) and the case was I forgot to install. Reinstalling the packages may not be too bad an idea.

---

### Post by ny_NEx on 2007-06-01
I have the same problem..... my gtk+-2,0.pc is located /usr/lib/pkgconfig and content of file is 


prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib
includedir=${prefix}/include
target=x11

gtk_binary_version=2.10.0
gtk_host=i486-pc-linux-gnu

Name: GTK+
Description: GIMP Tool Kit (${target} target)
Version: 2.10.11
Requires: gdk-${target}-2.0 atk cairo
Libs: -L${libdir} -lgtk-${target}-2.0 
Cflags: -I${includedir}/gtk-2.0 



Any suggestion ? PLEASE :)

---

### Post by magnusvv on 2007-06-09
You need to install libgtk2.0-dev.  It has the header files that your source is looking for to compile.

---

### Post by arnab.bhaumik on 2007-07-09
the last post works for me...........


arnab/vu2bpw:lolflag:

---

### Post by angusk on 2007-08-03
Thanks magnusvv that did the trick for me 
AnGus

---

### Post by ant2ne on 2007-09-18
```
antsvr@antubuntu:~$ sudo apt-get install libgtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtk2.0-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
antsvr@antubuntu:~$ 

```
but
```
antsvr@antubuntu:~/c$ gcc gtktest.c -o gtktest `pkg-config --cflags --libs gtk+-2.0`
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found

```So that didn't fix me.

Advice please.

---

