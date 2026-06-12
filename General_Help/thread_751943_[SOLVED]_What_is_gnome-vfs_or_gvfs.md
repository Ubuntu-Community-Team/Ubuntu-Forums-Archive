---
title: "[SOLVED] What is gnome-vfs or gvfs?"
date: 2008-04-11
forum: General Help
---

### Post by harrybazeegar on 2008-04-11
In some thread I read:

> 
gnome-vfs and now gvfs - I can seemlessly use totem/gedit/whatever over my LAN!


so
1. what is this gnome-vfs / gvfs
2. why may I want to use it?
3. how to install it
4. how to use it

---

### Post by hellblade on 2008-04-11
1. They are both a way to use foreign filesystems like local ones. eg. you can browse an ftp server without mounting it and open, edit and save a file with any compatible application on your computer, as if it was stored on your hard drive.
gnome-vfs is an old technology which had many quirks thus it didn't became popular. gvfs is it's replacement.

2. Instead of using various specialized applications to access that kind of filesystems, you simply access the files directly using gvfs. I'm not sure if it's supported yet but a feature would be the ability to access files stored inside archives (tar.gz, rar, zip etc.) directly from any program you want.

3. It should be installed automatically along with gnome as it is a core element of it. I think it's a gnome 2.22 technology

4. I am not a gnome user but I guess that you won't have to do something special to use it, as long as you have a gnome version that includes it. I mean that if it's installed (should be by default), then when you double click a link to an ftp destination, or something like that, nautilus should open it and allow you to browse it and do whetever you would expect from a local fs.


I am using kde which has a something similar called "kio" as in kde input output, and I can tell you you will love it as it makes a lot of things very simple.

Check this [http://www.gnome.org/~alexl/presentations/guadec2007-gvfs.odp](http://www.gnome.org/~alexl/presentations/guadec2007-gvfs.odp) for an overview by it's developers.

---

