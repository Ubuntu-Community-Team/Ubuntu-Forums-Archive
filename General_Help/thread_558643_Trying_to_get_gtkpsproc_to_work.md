---
title: "Trying to get gtkpsproc to work"
date: 2007-09-24
forum: General Help
---

### Post by bitpicker on 2007-09-24
Hello,

I hope this is in the correct section of the forums.

I'm trying to get a program called gtkpsproc to work. It is a program which can preprocess a file using a virtual printer, so that you can, for instance, rearrange the pages so that you can print a booklet with the pages in the correct order. It can be found at [www.rastersoft.com](www.rastersoft.com).

In the archive I have found a thread in which someone mentions using this program in Edgy:

[http://ubuntuforums.org/showthread.php?t=278530&highlight=gtkpsproc](http://ubuntuforums.org/showthread.php?t=278530&highlight=gtkpsproc)

Now I am trying to get it to run in Feisty, but its Gnome applet won't be loaded; if I try to add it to the panel an error message appears saying the applet was terminated unexpectedly, giving me the option to load it again or not, and if I load it again, the same error appears. (I'm not quoting the exact error message because it is in German)

The applet is a daemon written in Python which must run in order for the virtual printer to work. There is an option to start the Python script by hand with an option 'standalone' but that results in a segmentation fault (core dumped).

Is there anyone here who is using this program in Feisty successfully, and who can tell me what to do in order to make it work?

---

### Post by bitpicker on 2007-09-25
Thread marked solved; the solution was pretty simple, the program only works correctly with Python 2.4, not 2.5. After installing 2.4 alongside 2.5 it now works ok.

---

