---
title: "Xorg XTest extension library"
date: 2007-12-19
forum: General Help
---

### Post by Garf on 2007-12-19
Hi.... I am trying to install a module for my Logitech G15 keyboard...

Basically I have the LCD screen working etc...

I am following the install instructions and the first thing that it says to do is go into the directory where the files have been extracted to and type "./configure"

I have done this and I get this message at the end of it...**configure: error: "Xorg XTest extension library not found.  please install it"**

After the first time I ran .configure I installed *libxcb-xtest0* 

I tried it again and still the same message, so I then installed *libxcb-xtest0-dev*

Tried it again and it still didn't work... Not knowing if it had something to do with X server needing a restart or not, I restarted X and tried again, still no luck... I restarted the computer, still no luck..


I then found this page after a google search... [http://packages.ubuntu.com/feisty/libdevel/libxcb-xtest0-dev](http://packages.ubuntu.com/feisty/libdevel/libxcb-xtest0-dev)

On this page it tells me **This package contains the header and library files needed to build software using libxcb-xtest, the xtest extension for the X C Binding.**

So I still can't figure out what I have to do to get this ./configure to work...

Any help will be much appreciated.

---

### Post by atmtarzy on 2007-12-27
The package you're looking for is libxtst6.  I was having the same issues, but the ./configure worked fine after installing that.

-Drew

---

### Post by dethredic on 2008-01-01
> **atmtarzy said:**
> The package you're looking for is libxtst6.  I was having the same issues, but the ./configure worked fine after installing that.

-Drew

Thanks. I had the same problem and this worked.

---

