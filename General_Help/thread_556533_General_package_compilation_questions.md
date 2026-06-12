---
title: "General package compilation questions"
date: 2007-09-21
forum: General Help
---

### Post by kspider on 2007-09-21
I recently followed _[these]("http://wiki.gnucash.org/wiki/Debian")_ instructions to compile gnucash with ofxconnect enabled.  It all went fine and I'm happily downloading my banking records.  Here are some questions though.

1) This step: ```
sudo apt-get build-dep gnucash libaqbanking
``` installed 30 packages or so.  I don't plan on building this package again any time soon, so is it ok to remove all the packages it installed for build dependencies?  If so, is there a good way of determining what packages were installed simply for build dependencies?

2) I was really happy with my ability to use apt to get the packages I wanted until I built gnucash from source.  Now I realize that dpkg can do a lot more than I realized (the man page is sort of intimidating and there are a LOT of dpkg-<something> commands).  Can anyone recommend some good intro to dpkg reading?

3) When I run gnucash, it doesn't have a nice icon in its window list bar (at the bottom of the screen).  Is there a configuration file that allows you to define an icon?

Thanks a lot - Kspider

---

### Post by Happy_Man on 2007-09-21
1. It would *not* be a good idea to remove those packages. GNUcash needs those to run correctly. Removing them may hamper features or cause GNUCash to stop working altogether. 

2. Try here: [http://www.debuntu.org/2006/06/06/57-how-to-dpkg-guide](http://www.debuntu.org/2006/06/06/57-how-to-dpkg-guide)

3. Well, I think GNOME uses the icons that are specified in the menus. Try there to change the icon.

---

