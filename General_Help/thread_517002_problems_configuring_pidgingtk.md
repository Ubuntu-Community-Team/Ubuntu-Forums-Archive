---
title: "problems configuring pidgin/gtk"
date: 2007-08-03
forum: General Help
---

### Post by swinky on 2007-08-03
Hi, I'm new to the forums and still pretty new to Ubuntu itself.

I've been running Ubuntu 7.04 with a dual boot on my desktop and recently decided to take the plunge and run my laptop (IBM Thinkpad T40) entirely with Ubuntu.  But now I have a problem installing Pidgin, which I had previously installed on my desktop with no problems what-so-ever.

When I try ./configure for pidgin it says:
> You must have the GTK+ 2.0 development headers installed to compile Pidgin.
If you only want to build Finch then specify --disable-gtkui when running configure.

According to Synaptic I have libgtk2.0-dev installed (which correct me if I am wrong, but that would be the GTK+ 2.0 dev headers, right?) and I've tried reinstalling it but it doesn't help.   So I try to install GTK+ from the website, but when I try ./configure for GTK+ I get:
> checking for BASE_DEPENDENCIES... configure: error: Package requirements (glib-2.0 >= 2.12.0    atk >= 1.9.0    pango >= 1.12.0    cairo >= 1.2.0) were not met:

No package 'atk' found
No package 'pango' found
No package 'cairo' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Next I try ATK.  ./configure.  Once again, it ends with errors:
> configure: error:
*** GLIB 2.5.7 or better is required. The latest version of
*** GLIB is always available from [ftp://ftp.gtk.org/](ftp://ftp.gtk.org/). If GLIB is installed
*** but not in the same location as pkg-config add the location of the file
*** glib-2.0.pc to the environment variable PKG_CONFIG_PATH.

The problem here is that I already have glib 2.12.9 installed (configuring GTK even checks for it and doesn't complain.)  I don't really know where to go from here, as it keeps jerking me around in a circle.

---

### Post by apetresc on 2007-08-03
Your original issue is the strangest :( I would NOT recommend compiling and installing GTK on your own; it may conflict with the regular package (which, as I'm sure you realize, is quite an important library in Ubuntu!).

Have you tried: ```
sudo apt-get build-dep gaim
```
This will install all the necessary development packages for compiling gaim. I doubt that the move to Pidgin added any new library requirements, so this should be all you need (though, in fact, you already have libgtk2.0-dev, which is what the error message claims you're missing... but worth a try).

If that fails, do ```
apt-get source gaim
``` and try to compile the 2.0.0-beta5 Gaim that Ubuntu ships, which should be 95% identical to Pidgin. If that works but Pidgin fails, we'll have a diagnosis.

---

### Post by swinky on 2007-08-04
Gaim gave me the same error, claiming that the GTK+ 2.0 development headers aren't installed.  build-dep gaim didn't help either Pidgin or Gaim.

---

### Post by apetresc on 2007-08-04
Sorry, I can't reproduce that here. Theoretically speaking, "sudo apt-get build-dep gaim" should always give you whatever you need to build Gaim -- and on my box, it does (I just checked).

The only alternative I can think of is that you have some strange differences in repositories. Is there anything unusual in your /etc/apt/sources.list file?

---

### Post by swinky on 2007-08-04
My repositories are the default repositories, I've literally only had Ubuntu on this computer for the afternoon, and I haven't changed them.  They are all "feisty main restricted" "feisty universe" and "feisty-security universe" and all that sort of stuff... nothing that seems out of the ordinary. 

The only things that I have installed since installing Ubuntu are the updates that Ubuntu automatically updated, Mozilla Thunderbird, and I followed some but not all of the instructions for installing Ubuntu on a Thinkpad T40 from [http://www.cs.utexas.edu/users/walter/geek/linux-t40.html]("http://www.cs.utexas.edu/users/walter/geek/linux-t40.html").  Specifically, I followed the section on X windows and the Power Management (but I didn't mess with the scripting stuff.)  I wouldn't imagine that would have any effect on pidgin's ability to see GTK.

I'm wondering if it would just be easier at this point to try a fresh install?  Since I have only had it installed for a day it wouldn't be the end of the world, it would just take some time up tomorrow.  Like I said, I've hardly done anything to this install so I don't know what could have caused this problem.

---

### Post by swinky on 2007-08-04
Well, not sure what the problem was, but it's resolved.  I reinstalled Ubuntu, did all the things that I did last time (a bit more incrementally this time around), but I had absolutely no problems.  Pidgin installed just fine, so I am unsure of what the problem was under the last install.

---

