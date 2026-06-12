---
title: "Playground applet not working in Feisty"
date: 2007-04-21
forum: General Help
---

### Post by Vertelemming on 2007-04-21
Like so many people, I just upgraded to Feisty. No real troubles, except for this one inconvenience. I used to use gxmms for XMMS control without trouble. Finding it gone upon starting Feisty, I installed the replacement applet, Playground. The only problem is that it doesn't work. The plugin adds to the panel without trouble, but it doesn't seem to be able to control XMMS, and if I open up the Preferences window, none of the controls seem to function properly. If you close the Preferences window using the X, then it won't open up again until you remove and reload the plugin.

This isn't something astonishingly critical, as the XMMS status plugin mimics most of the functionality I use, but it would be nice to have the applet back. So, any ideas?

---

### Post by CeeC on 2007-04-23
Same here. I used to have gxmms-xmms or gxmms-bmp, but with feisty we have now playground applet and doesn't work at all. I have installed playground-plugin-xmms too, but playground can't control my xmms.

---

### Post by onlynux on 2007-05-02
same here too. ](*,) ](*,)

---

### Post by onlynux on 2007-05-02
so, it's good for me:) 
i've removed playground with synaptic and install playground with the tar.gz find here [http://home.gna.org/playground/]("http://home.gna.org/playground/")

for playground :
./configure --prefix=/usr --with-gconf-schema-file-dir=/usr/share/gconf/schemas
make
sudo make install

see when configure if you have some lib like libglade2 etc 

for playground-xmms  :

./configure --prefix=/usr
make 
sudo make install

you must have xmms-dev intalled !!

I'm happy my feisty is now perfect.........

---

### Post by CeeC on 2007-05-02
Yeah, it works for mee too. Thx mate :)

I hope the fixed soon in repositories. I reported the bug to Ubuntu:
[https://bugs.launchpad.net/ubuntu/+source/playground/+bug/109744](https://bugs.launchpad.net/ubuntu/+source/playground/+bug/109744)

---

### Post by dys4ic on 2007-06-18
> **onlynux said:**
> so, it's good for me:) 
i've removed playground with synaptic and install playground with the tar.gz find here [http://home.gna.org/playground/]("http://home.gna.org/playground/")

for playground :
./configure --prefix=/usr --with-gconf-schema-file-dir=/usr/share/gconf/schemas
make
sudo make install

see when configure if you have some lib like libglade2 etc 

for playground-xmms  :

./configure --prefix=/usr
make 
sudo make install

you must have xmms-dev intalled !!

I'm happy my feisty is now perfect.........

Nice...the same thing goes for beep media player, beep-media-player-dev is required to install the plugin.

---

