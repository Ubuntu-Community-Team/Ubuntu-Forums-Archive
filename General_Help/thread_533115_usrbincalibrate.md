---
title: "/usr/bin/calibrate"
date: 2007-08-23
forum: General Help
---

### Post by 0li on 2007-08-23
I need the application /usr/bin/calibrate on a ubuntu 6.06 installation. Is there a clean way to install it on ubuntu?




I was able to make it work by doing the following but it breaks the software index.

1 ) I found another server that had xi1.0.so (which calibrate needs). I made a .tar.gz of it and installed in /usr/lib/TkXInput.

     $ sudo ldconfig
 
2) sudo apt-get tkxinput
 
        I get a messages that says tkxinput is not available, but is referred by another package.
 

3) Alright so I just download tkxinput_1.0-3_i386.deb

        $ sudo dpkg -i tkxinput_1.0-3_i386.deb

        Here it unpacks tkxinput (/usr/bin/calibrate is installed) but it complains the it depends on xlibs and cannot be configured.

4) $ /usr/bin/calibrate

         cool, it works.

The problem now is that I cant run apt-get or "software updates" anymore because my software index is broken.

How can I get out of it? The only way I was able to get /usr/bin/calibrate was by hacking my way until it worked. Now the clean way of installing software is completely broken because of this, what should I do ?

<rant> I mean we didn't have these problems with ./configure; make; make install, did we ? </rant>

---

