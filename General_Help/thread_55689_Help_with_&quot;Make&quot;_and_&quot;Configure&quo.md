---
title: "Help with &quot;Make&quot; and &quot;Configure&quot;"
date: 2005-08-09
forum: General Help
---

### Post by wadesmart on 2005-08-09
08092005 2007 GMT-5

I have a requirement for a onscreen ruler and I found  gruler-0.6. I downloaded it and it has some generic build instructions. 

It says to cd to the file and then type ./configure. When I do this I get an error: "Configure: error: no acceptable C compiler found in $PATH"

So, does this mean that I do not have a compiler?
That I need to move this folder someplace else to compile?
Or what?

Im going to make a big assumption that Ubuntu doesnt have a compiler installed and that I have to get one. If that is correct, what would I get?

Thanks

Wade

---

### Post by PeP on 2005-08-09
[QUOTE=wadesmart]08092005 2007 GMT-5

I have a requirement for a onscreen ruler and I found  gruler-0.6. I downloaded it and it has some generic build instructions. 

It says to cd to the file and then type ./configure. When I do this I get an error: "Configure: error: no acceptable C compiler found in $PATH"

So, does this mean that I do not have a compiler?
That I need to move this folder someplace else to compile?
Or what?

Im going to make a big assumption that Ubuntu doesnt have a compiler installed and that I have to get one. If that is correct, what would I get?

Thanks

Wade[/QUOTE]

launch synaptic
select search
search for gcc
install it

hint : kruler is available through synaptic ...

---

### Post by varunus on 2005-08-09
Don't just install gcc, install the package build-essential; that will include "make"

You'll probably also need some dependencies; I'm going to guess libgtk2.0-dev, at least.  If ./configure complains about missing dependencies, you'll need the .deb package.

Also, try the software "checkinstall" from synaptic.  If you run "sudo checkinstall" instead of "sudo make install" when compiling programs, it will make a .deb package that you can share and later uninstall with synaptic if you need to!

---

### Post by wadesmart on 2005-08-09
08092005 2058 GMT-5

Thanks for that information. 

I installed what you said Varunus and then I did ./configure and I got another error: 

checking for libgnomeui-2.0 gtk+-2.0 libglade-2.0... Package libgnomeui-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing 'libgnomeui-2.0.pc' to the PKG_CONFIG_PATH environment variable
No package 'libgnomeui-2.0' found.

Ok. Went back to Synaptic and I did find that package.
There is a libgnomeui-0 and a -0-dbg and then a and a libgnomeui32 but not a -2.0. 

Wade

---

### Post by varunus on 2005-08-09
Well, it seems ./configure wants libgnomeui.  What this means is that it wants the corresponding -dev package from synaptic.  so search for libgnomeui, find the closest-named deb package (in this case libgnomeui-dev) and install it.  It seems from that output you'll also need libgtk2.0-dev and libglade2-dev.  The names can vary some, but you'll need the dev package for all of the dependencies; this lets the program compile.

---

### Post by wadesmart on 2005-08-09
08092005 2109 GMT-5

Oh.... never mind. I found a note saying I need ibgnomeui-dev installed for this error. 

Thanks. 

Wade

---

### Post by wadesmart on 2005-08-09
08092005 2117 GMT-5

Ok. Im a bit confused. 

I typed ./configure and that ran though a long listing ending with 
   config.status: creating po/Makefile

Then refering to your post, I typed "sudo checkinstall" and then another long list comes flashing on the screen. 

However, the information with the software (gruler) states type ./configure, then "make", then "make install". 

So, after I type sudo checkinstall and it runs through that list, do I type make install?

Wade

---

### Post by wadesmart on 2005-08-09
08092005 2126 GMT-5

Never mind. After the sudo checkinstall .... the messages answered my question. 

One last question though: How do I get it registered in the Applications list?

---

### Post by PeP on 2005-08-09
[QUOTE=wadesmart]08092005 2117 GMT-5


So, after I type sudo checkinstall and it runs through that list, do I type make install?

Wade[/QUOTE]
no you just made a .deb file.
install it wiith dpkg
sudo dpkg -i knvsfkjfbvgk.deb

---

### Post by varunus on 2005-08-09
Get the SMEG menu editor to add things to your menu.

[http://www.ubuntuguide.org/#menu-editor](http://www.ubuntuguide.org/#menu-editor)

Make sure to enable extra repositories as per the guide's instructions before installing smeg.

Also, you should have typed "make" before typing "sudo checkinstall" (make will compile, checkinstall makes a .deb package) so I don't know if its actually installed properly.  You may want to uninstall the .deb package and then redo it, this time typing;

./configure
make
sudo checkinstall

---

### Post by wadesmart on 2005-08-09
08092005 2222 GMT-5

Hey, I really appreciate you guys (hum...not politically correct is it) for helping me out. I got it installed and running and the menu's are all straight. 

I had installed Opera some time back and it was under Other... strange I thought so I moved it to Internet. 

Again, thanks. 

Wade

---

