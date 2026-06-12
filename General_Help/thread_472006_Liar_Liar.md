---
title: "Liar Liar"
date: 2007-06-12
forum: General Help
---

### Post by golfy on 2007-06-12
Hi,

I am new to Ubuntu and was wondering if anyone could guide me through the installation of Liar Liar software [http://liarliar.sourceforge.net/](http://liarliar.sourceforge.net/) - I am using a Live CD. I have it in a zipped format and have unzipped it into a folder but am stuck from that point.

Thanks

Dave

---

### Post by cookies on 2007-06-12
Go to Applications > Accessories > Terminal

Now type cd and the path to the folder the stuff is in

So, if it is on your desktop, it's cd /home/USERNAME/Desktop/liarliar-0.5.2

On the live cd the USERNAME is ubuntu

now type 

sudo aptitude update 

Wait till it finshes

then type

sudo aptitude install build-essential checkinstall 

Now type

./configure

After it finishes and it's all good, type:

make

then after that finishes and it's all good, type

sudo make install

Hope it's all good and works out for ya.

---

### Post by golfy on 2007-06-13
Hi Cookies,

I'll give that a go today.

Thanks a lot for your help, much appreciated.

Regards

Golfy

---

### Post by JorjGaidin on 2008-02-01
So I've been trying for about a week to get this thing compiled, but I just haven't made it yet.  I'm getting stuck on the configure part.

Here is the output of the error...

checking for gtkmm-2.0 gthread-2.0 gstreamer-0.6... Package gstreamer-0.6 was not found in the pkg-config search path. Perhaps you should add the directory containing `gstreamer-0.6.pc' to the PKG_CONFIG_PATH environment variable No package 'gstreamer-0.6' found
configure: error: Library requirements (gtkmm-2.0 gthread-2.0 gstreamer-0.6) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

I believe ubuntu uses the package totem-gstreamer right?  Why can I not get this to work?

HELP!

---

