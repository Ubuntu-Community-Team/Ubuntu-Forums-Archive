---
title: "What do the folders mean?"
date: 2008-06-29
forum: General Help
---

### Post by jamesdcarroll on 2008-06-29
I'm moving from Windows and am a VB/Java programmer.  I'm very comfortable with the 'special' folders (Program Files, sys32, etc) and other things related to installing applications (the registry in particular) and managing users.  On the Ubuntu/Linux side though, I'm confused. Its obvious that folders like home and usr and bin and the rest *mean* something and have a purpose. The documentation though seems to either assume that you are a pure user and willing to let Ubuntu do its thing or a C programmer raised on a command line. 

Are there any tutorials/doc that kinda hits that sweet spot half way between those two extremes?

Thanks,

---

### Post by starcannon on 2008-06-29
This guide looks pretty good, try it out to start with perhaps.

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/Linux-Filesystem-Hierarchy.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/Linux-Filesystem-Hierarchy.html)

I know I've seen links posted to other guides here in the forums, perhaps do a little searching and digging with the forum search tool.

Welcome to Ubuntu and GL

---

### Post by Miljet on 2008-06-29
Here is another link to the file system.
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
From what I have found, these standards aren't set-in stone. Various distributions sometimes store files in different directories. I have come to realize that most system configuration files are kept under /etc or sub-directories of it.

---

### Post by jamesdcarroll on 2008-06-29
Thank you both very much... tldp.org looks really good.

---

### Post by theshadowwithanmp5n on 2008-06-29
whatever you do, be careful when editing folders in the /etc directory (that's what we call them)
/usr/bin and /usr/sbin are the equivalents of the Program Files folder under windows
/home is the equivalent of documents and settings
and unlike windows, everything is treated as a file. hard disks, drivers, everything.
and you should get familiar with the terminal, it's your lifeline. it's not like the windows command prompt which isn't as complex or vital.
hope this is of great help to you.

---

