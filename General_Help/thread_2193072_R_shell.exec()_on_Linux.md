---
title: "R: shell.exec() on Linux"
date: 2013-12-11
forum: General Help
---

### Post by dovah on 2013-12-11
Hello! 

I'd like to ask if somebody of you knows a Linux command which could replace the shell.exec() used in Windows in order to open a webpage from the R console. I'm running on Ubuntu 12.04LTS, Gnome desktop. 

(I know I can do it from terminal by using $firefox +url, but could be useful to ask R without an application switch)

Thank you =;

---

### Post by drmrgd on 2013-12-11
It might be helpful to know what your final goal is as there are quite a number of relevant webpage and URL specific R commands.  shell.exe() will open whatever file you pass to it, using the program assigned it by the Windows Registry.  I guess an equivalent on the Linux side would simply be system():

[http://stat.ethz.ch/R-manual/R-devel/library/base/html/system.html](http://stat.ethz.ch/R-manual/R-devel/library/base/html/system.html)

With regard to URL specific commands, though, there is a base function called browseURL() that will open a webpage in a browser window from the R console:

```

browseURL("http://www.google.com")

```

[http://stat.ethz.ch/R-manual/R-devel/library/utils/html/browseURL.html](http://stat.ethz.ch/R-manual/R-devel/library/utils/html/browseURL.html)

If you just want the data from a webpage to put into something like a dataframe, you can also use one of the read functions like read.table.url(), and I think you could even hack something out with scan() if you wanted.

---

### Post by dovah on 2013-12-11
Thank you for your answer! :D

---

