---
title: "widgets, customizing, and other questions on fluxbox"
date: 2005-07-24
forum: General Help
---

### Post by tlo on 2005-07-24
im running fluxbox on kubuntu, and it looks cool, but im having problems getting a few things to work. first of all, im trying to download a new theme, but they're all tar.gz files. i've only ever apt-get'd files, i've never downloaded and installed myself, how do i do that with a tar.gz? also where can i get widgets (cpu load, memory usage, etc) and how do i install them? one more, is there a way to use virtual desktops, like in enlightenment?

---

### Post by majikstreet on 2005-07-24
[QUOTE=tlo]im running fluxbox on kubuntu, and it looks cool, but im having problems getting a few things to work. first of all, im trying to download a new theme, but they're all tar.gz files. i've only ever apt-get'd files, i've never downloaded and installed myself, how do i do that with a tar.gz? also where can i get widgets (cpu load, memory usage, etc) and how do i install them? one more, is there a way to use virtual desktops, like in enlightenment?[/QUOTE]
 Hi,
For tar.gz files you need to do this after you've saved it:
```

cd /path/to/file
tar zxf filename.tar.gz

```
That will extract the files to the a directory called "filename" in wherever you saved the file.
I don't think that is how you install a fluxbox theme though, sorry.

For widgets here is a great site: [http://gdesklets.gnomedesktop.org/](http://gdesklets.gnomedesktop.org/)

You can use them on any window manager-- you just apt-get install gdesklets and you have the base program.

There is a wonderful HOWTO about gdesklets right here: [http://www.ubuntuforums.org/showthread.php?t=31928&highlight=gdesklets](http://www.ubuntuforums.org/showthread.php?t=31928&highlight=gdesklets)

For the fluxbox virutal desktops, here is an article about using fluxbox I found on google: [http://www.linux.org/lessons/short/fluxbox/](http://www.linux.org/lessons/short/fluxbox/)

majikstreet

---

### Post by dave9191 on 2005-07-24
Hey, Fluxbox rocks :) 

A tar.gz file is a compressed archieve file. Similar to a .zip file. You need to uncompress it. I cheat and run konqueror and right click on them and pick extract. But you can do it with the command line using the tar command and serveral arguments that I always forget. Withing the extracted files you might see a README file or an INSTALL file which should tell you what to do. If not and you only find a text file then move that to your fluxbox sytle dir (probably /usr/share/fluxbox/styles). Note that you need to copy the files over as root, so from a root file browser or using "sudo cp ...." command. 

You can get apps for the slit from [http://dockapps.org/](http://dockapps.org/) . There are also other sites, I think there are others mentioned in the fluxbox documentation. [http://fluxbox.sourceforge.net/docs/en/newdoc.index.php](http://fluxbox.sourceforge.net/docs/en/newdoc.index.php) . I recommend that you read that a read sometime, or at least a browse. Its not too long. 

As for installing them, some you can find in the repositories, you can apt-get them. Others will come with a .deb file (you can isntall using dpkg -i package_name.deb). But some you will have to compile youself. To compile extract the tar file and go to the directory. Fire run ./configure , that will tell you if your system has what you need to compile. If that passes with no errors compile it using the "make" command. If that passes with no errors then "sudo make install" to copy the compiled program to your system.

As for the virtual desktops, you can create new workspaces from either the right click menu or middle click menu on the desktop. You can switch to them using the keyboard shortcut, or the arrows in the toolbar. Also you can install a pager if you want to see how many desktops and whats on them. 

And dont forget to assign keybaord shortcuts for things that you want to do. I have no need to touch the mouse unless Im browsing. I launch every program I need from a keybaord shortcut. 

If you need anything else, just ask :)

Dave

---

