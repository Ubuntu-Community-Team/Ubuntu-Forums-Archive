---
title: "help install candido engine"
date: 2006-12-03
forum: General Help
---

### Post by m.musashi on 2006-12-03
I keep getting this error in a terminal window when I do anything that has a theme related function - gnome-screenshot for example.
```
(gnome-panel-screenshot:23745): Gtk-WARNING **: Unable to locate theme engine in module_path: "candido",
/home/jim/.themes/Candido-DarkOrange/gtk-2.0/gtkrc:161: error: invalid string constant "theme-button", expected valid string constant
```
so I assumed I needed to install the candido engine. I found and installed the engine using
```
sudo dpkg -i gtk2-engines-candido_0.9-1_i386.deb
```
It installed fine (i.e. no errors) but I still get the error. According to the website, I need to do this
```
Installation Instructions:
After the extraction of the file, go in the source dir and compile as following:

./configure --prefix=/usr --enable-animation
make
make install
```
but the first line just returns an error about no such file or directory. Obviously I'm doing something wrong. I'm still very much a noob - especially when having to install manually. Can anyone point out the error of my ways?

Thanks.

---

### Post by maddog39 on 2006-12-03
Yea, you got the error doing./configure because you need the source code package, in other words, the .tar.gz file from their website. The .deb is a debian package and if it didnt work, you need to compile the source code usin g the method on their website. Just download the .tar.gz package, unpack it, and cd to the directory where the files were unpacked. THen, you do ./configure && make && sudo make install

---

### Post by m.musashi on 2006-12-03
Thanks. I think I understand a bit better. It seemed to install fine this time and I don't get the error about the engine, but I still get this error
```
/home/jim/.themes/Candido-DarkOrange/gtk-2.0/gtkrc:161: error: invalid string constant "theme-button", expected valid string constant
```
Is this because of a flaw in the theme or a flaw in how I have installed something?

---

