---
title: "[SOLVED] Help with AWN"
date: 2008-06-24
forum: General Help
---

### Post by jeremy1138 on 2008-06-24
I just installed AWN and it seems to be working fine but for some reason I can't figure out how to get applets installed.  I followed the instructions here:

[http://linuxhelp.blogspot.com/2008/02/cool-awn-applets-to-adorn-your-ubuntu.html](http://linuxhelp.blogspot.com/2008/02/cool-awn-applets-to-adorn-your-ubuntu.html)

The page suggested that I edit my sources.list file to include
```

#FILE: /etc/apt/sources.list
deb http://ppa.launchpad.net/reacocard-awn/ubuntu gutsy main

```
and then run
```

$ sudo apt-get update
$ sudo apt-get install awn-core-applets-bzr

```
but that messed things up so that I couldn't get AWN to work at all until I uninstalled it using synaptic package manager.  I also looked here:

[http://wiki.awn-project.org/Applet_Gallery](http://wiki.awn-project.org/Applet_Gallery)

but the web page doesn't seem to be working correctly...  Most of the links don't seem to be working correctly; about all I could do was download some of the applet icons (.png images).  Any ideas?  Thanks in advance for the help!

---

### Post by Enlitend on 2008-06-24
If I recall it correctly, there are 2 vesrions of awn out there. 
This thread may help you:

[http://http://ubuntuforums.org/showthread.php?t=749749]("http://ubuntuforums.org/showthread.php?t=749749")

---

### Post by jeremy1138 on 2008-06-24
> **Enlitend said:**
> If I recall it correctly, there are 2 vesrions of awn out there. 
This thread may help you:

[http://http://ubuntuforums.org/showthread.php?t=749749]("http://ubuntuforums.org/showthread.php?t=749749")

That did it!  Thanks very much for your help!

---

### Post by Enlitend on 2008-06-24
Glad it works for you. :)

---

