---
title: "No package 'pygtk-2.0' found"
date: 2008-07-07
forum: General Help
---

### Post by chaosdesigner on 2008-07-07
Hi guys,

This is probably a really stupid question but im new to Ubuntu so i dont know what to do... Im installing the kiba-dock right now and after i ran "./autogen.sh --prefix=/usr --libdir=/usr/lib64" i got this error message:


No package 'pygtk-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PYGTK_CFLAGS
and PYGTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


First i just tried to find the package 'pygtk-2.0', which is apparently needed, in Synaptic Package Manager but i wasnt successful. even after i googled 'pygtk-2.0' i didnt come to an answer, so could anybody pls tell me how to get this package, or how i can "set the environment variables PYGTK_CFLAGS and PYGTK_LIBS to avoid the need to call pkg-config" ...


thx for your help,

chaosdesigner

---

### Post by brian_p on 2008-07-07
> **chaosdesigner said:**
> First i just tried to find the package 'pygtk-2.0', which is apparently needed, in Synaptic Package Manager but i wasnt successful. even after i googled 'pygtk-2.0' i didnt come to an answer, so could anybody pls tell me how to get this package, . . . .

A rose by any other name etc, etc

```
apt-cache search pygtk
```

---

### Post by chaosdesigner on 2008-07-07
yeah then i get a list of packages ... but what now?

there is no package named  pygtk-2.0..

---

### Post by brian_p on 2008-07-07
> **chaosdesigner said:**
> yeah then i get a list of packages ... but what now?

there is no package named  pygtk-2.0..

No - but there are packages with the letters p, y, g, t and k in them. In that order. And with a 2.

---

### Post by nikgare on 2008-07-07
And if your compiling something against it you'll also &#324;eed the corresponding **-dev** files

---

### Post by chaosdesigner on 2008-07-07
mh these are the only ones that might be it and they all dont bring anything ...

python-gtk2 - Python bindings for the GTK+ widget set
python-gtk2-dev - GTK+ bindings: devel files
python-gtk2-tutorial - tutorial for the GTK2 python library


but maybe could someone help me with this:

Alternatively, you may set the environment variables PYGTK_CFLAGS
and PYGTK_LIBS to avoid the need to call pkg-config.

mh yeah but thx for all ur help sofar

Edit: Im trying to install python-gtk2-dev but I get this message:

The following packages have unmet dependencies:
  python-gtk2-dev: Depends: python-dev but it is not going to be installed
                   Depends: python-gobject-dev (>= 2.14) but it is not going to be installed

---

### Post by brian_p on 2008-07-07
> **chaosdesigner said:**
> but maybe could someone help me with this:

Alternatively, you may set the environment variables PYGTK_CFLAGS
and PYGTK_LIBS to avoid the need to call pkg-config.

I don't compile programs so am little use to you. 

> Edit: Im trying to install python-gtk2-dev but I get this message:

The following packages have unmet dependencies:
  python-gtk2-dev: Depends: python-dev but it is not going to be installed
                   Depends: python-gobject-dev (>= 2.14) but it is not going to be installed

If you have read the package description I think you will agree this is what you want. Both python-dev and python-gobject-dev are listed at packages.ubuntu.com but perhaps they are temporarily unavailable. Leave it until tomorrow or download and install them with dpkg -i <package>.

---

### Post by chaosdesigner on 2008-07-08
Oh this is so confusing ...

Now when i want to install Python-dev it says:

Depends: python2.5-dev but it is not going to be installed

alright, so now i tried to install python2.5-dev, but then he says:

Depends: python2.5 (=2.5.2-2ubuntu4) but 2.5.2-2ubuntu5 is to be installed

So right, i just need to upgrade it, but my python2.5 is already version 2.5.2-2ubuntu5 ...

---

### Post by nikgare on 2008-07-08
oOu could try using **aptitude** instead of Synaptic to install - it tends to be a bit more intelligent.

---

### Post by chaosdesigner on 2008-07-08
thank you it worked with aptitude and now my programm runs too, big thanks.

---

### Post by chiroptera on 2009-02-04
can someone please tell me how to install pygtk-2.0?  I get the following result when I type apt-cache search gtk, so it seems like it's already installed.  However, when trying to install another package, gnome-python-extras, which I needed to install a text editor, Scribes, it says :

checking for PYGTK... configure: error: Package requirements (pygtk-2.0 >= 2.4.0) were not met:

No package 'pygtk-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PYGTK_CFLAGS
and PYGTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


If anyone could provide an idiot-proof method of intalling the required gtk package here, I would really appreciate it..

---

### Post by chiroptera on 2009-02-04
Forgot: this is what happens when I type cache search: 
~# apt-cache search pygtk
python-glade2 - GTK+ bindings: Glade support
python-gnome2 - Python bindings for the GNOME desktop environment
python-gnome2-dev - Python bindings for the GNOME desktop environment
python-gtk2 - Python bindings for the GTK+ widget set
python-gtk2-dev - GTK+ bindings: devel files
python-gtk2-tutorial - tutorial for the GTK2 python library
python-gtksourceview2 - Python bindings for the GtkSourceView widget
claw4 - Chris's Lame File Browser
comix - GTK Comic Book Viewer

etc...Thanks!

---

### Post by prasanthp on 2009-11-09
> **chaosdesigner said:**
> thank you it worked with aptitude and now my programm runs too, big thanks.
hello [chaosdesigner]("http://ubuntuforums.org/member.php?u=610080")

    I am having the same error. 


 Package requirements (pygtk-2.0 >= 2.10.3) were not met:

No package 'pygtk-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PYGTK_CFLAGS
and PYGTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


Can you tell exactly how you come out of the error.

Thanks in advance

---

### Post by neo unplugged on 2010-08-30
Hi,
Check this link,
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=801695](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=801695)

it worked for me :D

---

