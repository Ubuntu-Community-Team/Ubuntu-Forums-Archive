---
title: "[SOLVED] Is there a Flash creating software alternative for Ubuntu?"
date: 2007-07-02
forum: General Help
---

### Post by RonB123123 on 2007-07-02
Is there a Flash creating software alternative for Ubuntu?

I've looked over Google and on this site, but I couldn't find it. If there is such a free/(free opensource) software that can compile to .flas and .swfs and can process ActionScript, please post! Thank you! ;)

---

### Post by southernman on 2007-07-02
google blender 3d... I think that'll do what you need.

It should be in add/remove and synaptic.

---

### Post by Lord Illidan on 2007-07-02
Or try the windows software in wine.

---

### Post by John.Michael.Kane on 2007-07-02
This may help.

[swftools]("http://linuxappfinder.com/package/swftools")

[vnc2swf]("http://linuxappfinder.com/package/vnc2swf")

[drawswf]("http://linuxappfinder.com/package/drawswf")

[animestudiopro]("http://linuxappfinder.com/package/animestudiopro")

---

### Post by izak on 2007-07-17
I'm writing a flash game in Ubuntu dapper at the moment.

Head over to [www.osflash.org](www.osflash.org)

Basically I use actionscript 2 with two compilers: swfmill and mtasc. A Linux executable for mtasc is available. swfmill you'll have to build form source (i think it is similar to swftools, but the tutorials on osflash describe the use of the swfmill+mtasc combination). The newest version of swfmill has support for svg. This means you can use the excellent Inkscape to draw vector graphics and incorporate them into your swfs. You'll just have to install the relevant dependencies, which are all available throught synaptic. 

For an editor, I've struggled finding one with actionscript code highlighting, folding and completion. But I've found the solution. Below is my post to the osflash mailing list:

> Hi

I've come upon this thread as I also was struggling with finding an editor in Linux. I tried eclipse+ASDT, but the I couldn't get it working properly. Also eclipse is too heavy and slow for my tastes and I can't customise it to use makefiles for building.

I normally use Scite, an exellent, lightweight customisable graphical editor with support for many languages and code completion. Also it is available form the standard repositories on my Ubuntu installation.  Since Scite|Flash is available for Windows, I managed to use their configuration files to get the same features for the Linux scite.

First, download and install scite|flash for windows to get access to the files included in the installation. Copy the flash.properties flash.api and (not sure if these are necessary) API.custom API.flashcommClient API.flashcommServer from the windows installation to where your Linux installation lives. For me this is in /usr/share/scite.

Next edit your SciteGlobal.properties file (it might be possible and wiser to add this to the sciteuser.porperties instead(?)). Add the folowing:

import flash

Uncomment this if you want autocompletion:

autocompleteword.automatic=1

If you want to add flash the the language selection menu, add this to the "menu.language=\" entry:
Flash|as||\ 

With these changes you will have syntax highlighting, code folding and completion for actionscript.

In flash.properties, change:
lexer.$(file.patterns.flash)=flash
to 
lexer.$(file.patterns.flash)=cpp
since the linux version of scite doesn't have a flash lexer and the syntax structure for flash is the same is cpp.

Also if you want auto completion and calltips for actionscript, change the line in flash.properties referring to the api  to:

api.$(file.patterns.flash)=$(SciteDefaultHome)/flash.api;

Note the '/' . The default in flash.properties is '\' which doesn't work for linux. After this is changed autocompletion and calltips work like they did in scite|Flash for windows!

Lastly, I prefer to use makfiles, so I edited the Commands section of my flash.properties file to contain:

command.compile.$(file.patterns.flash)=make 

and nothing else.

I hope this helps other linux users. Scite is really excellent; I use it for python and c coding (and now flash/actionscript).

I haven't tested whether it will interpret the compiler output errors to take you to the right line. But with a bit of tinkering I'm sure it's possible...

Cheers
Izak

I've tested it and scite also goes to the correct line where the error is.
Hope this helps!

---

### Post by fragos on 2007-07-17
Check out ffmpeg from the Ubuntu repositories.  I've used it to from .flv flash files to other formats like .mpg or .avi.  I haven't tried going to flash from other formats.  It's a popular command line video conversion tool.

---

