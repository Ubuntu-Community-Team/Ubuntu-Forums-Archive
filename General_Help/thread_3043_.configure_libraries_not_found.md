---
title: "./configure libraries not found"
date: 2004-11-02
forum: General Help
---

### Post by freefood on 2004-11-02
I'm trying to install Gnomad2 for my Creative Nomad mp3 player.  However, whenever I run ./configure, I get the following output:

> checking for         glib-2.0                    gthread-2.0                 gtk+-2.0                    libgnomeui-2.0         libnjb                  id3tag... Package glib-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `glib-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'glib-2.0' found

configure: error: Library requirements (        glib-2.0                    gthread-2.0                 gtk+-2.0                    libgnomeui-2.0             libnjb                   id3tag) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
However, I'm pretty sure all this stuff is installed, particularly glib, gtk, and libnjb - they all show up as installed on Synaptic.  How can I get the config to find these libraries?

---

### Post by stodge on 2004-11-02
Are you sure you have the correct version installed? There may be a glib 1.0 and a 2.0.

---

### Post by JProgrammer on 2004-11-02
You not only need these packages but to compile against them you need their -dev equivalents eg glib2-dev, gtk2-dev etc.

---

### Post by FLeiXiuS on 2004-11-02
[QUOTE=JProgrammer]You not only need these packages but to compile against them you need their -dev equivalents eg glib2-dev, gtk2-dev etc.[/QUOTE]

And also libgtk2-dev.

---

### Post by natefish on 2004-11-09
Freefood and others, let me know how this goes. I was able to install Gnomad2 from debian repository and from souce, it works great but only when I launch from the command line as root user. There is some kindof permission issue for the jukebox that only allows it to be accessed by root user. I have another thread where I am looking for answers to this problem. 

[http://www.ubuntuforums.org/showthread.php?t=2700](http://www.ubuntuforums.org/showthread.php?t=2700)

---

