---
title: "Evolution: Remove attachments from single\multiple emails"
date: 2007-10-26
forum: General Help
---

### Post by drumour on 2007-10-26
Have trawled around the web and found one site which seems to have a 'plugin' to do this - it appears to do it for a single message (even that would be welcome) but it A) needs compiling and B) is beyond my comprehension!

[http://people.debian.org.tw/~chihchun/2006/10/23/remove-attachments-plugin-for-evolution-00/](http://people.debian.org.tw/~chihchun/2006/10/23/remove-attachments-plugin-for-evolution-00/)

Have I missed something? My .evolution folder is 256MB and risinng - will I have to delete the  message to get rid of the attachments

---

### Post by drumour on 2007-11-03
link provided appears to no longer work. Below is the pertinent text from the page and link to file. Hope this helps someone as it is beyond me:

This plugin is pretty small, it’s about 150 lines of C code. You can download remove-attachments-0.0.1.tar.gz from this url. I did not provide a makefile for build it, you have to put this plugin in evolution source tree. It will generate make file for compile this plugin, if you know how to modify the automake/autoconf config files.

Basically, you have to add the makefile path for the plugin in evolution/configure.in, and add a sub-directory in evolution/plugins/Makefile.am. After that, you have to execute autoconf and automake to update the configure script and makefiles.

link to file:
[http://people.debian.org.tw/~chihchun/wp-content/uploads/2006/10/remove-attachments-0.0.1.tar.gz](http://people.debian.org.tw/~chihchun/wp-content/uploads/2006/10/remove-attachments-0.0.1.tar.gz)

---

### Post by chihchun on 2008-07-02
Hi, there is a new version and Debian package available.

[http://people.debian.org.tw/~chihchun/2008/05/23/remove-attachments-evolution-plugin-002/](http://people.debian.org.tw/~chihchun/2008/05/23/remove-attachments-evolution-plugin-002/)

---

