---
title: "Gimp 2.4.3 and GTK+ Problems"
date: 2008-01-29
forum: General Help
---

### Post by Giant Speck on 2008-01-29
Okay.

First of all,I am a total Linux n00b.  Just warning you before you continue reading this post.

I have Kubuntu 7.04, and I am *trying* to install Gimp v2.4.3.

Now, this involves compiling it, I guess.  I don't know.  It's all new to me. 
Anyway,  I downloaded the Gimp, extracted the tarball (I think I got the term right there) and ran ./configure after changing the directory to the Gimp folder.

The ./configure ran fine until it ran into the fact that I didn't have the right version of GTK+ installed on my computer.

So, I downloaded a new version from [ftp://ftp.gtk.org](ftp://ftp.gtk.org) and installed it.

However, when I went back to do ./configure with Gimp, the same problem came up.

Then I consulted the INSTALL file, and it said to remove the old libraries.  I interpreted this as deleting the GTK-2.0 directory in /usr/lib  (IF THIS WAS A HORRIBLE MISTAKE, PLEASE TELL ME NOW!).

I tried to do the ./configure in Gimp again, and it STILL didn't work.

I have no idea what I am doing and need help before I try to do something stupid and destroy my computer.  

Please? 8-[

---

### Post by jan quark on 2008-01-30
wouldn't it be easier to install gimp via the package manager?

I dont run Kubuntu but I guess there should be somthing similar to the Synaptic Package Manager in the menu

or 

you can install gimp via the terminal
just type into the terminal
```
sudo apt-get install gimp
``` here you will have to enter your login password

the advantage of using synaptic or apt-get is that all dependencies are installed automatically with the main application

compiling applications should not be used as the first install option


here a good guide how to install thing in ubuntu
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

I hope this helps a bit

---

### Post by jbman on 2008-01-30
the current package out is 2.4.2 so i am guessing why jan is trying to compile

---

### Post by supertails on 2008-01-30
> **jan quark said:**
> wouldn't it be easier to install gimp via the package manager?

I dont run Kubuntu but I guess there should be somthing similar to the Synaptic Package Manager in the menu

or 

you can install gimp via the terminal
just type into the terminal
```
sudo apt-get install gimp
``` here you will have to enter your login password

the advantage of using synaptic or apt-get is that all dependencies are installed automatically with the main application

compiling applications should not be used as the first install option


here a good guide how to install thing in ubuntu
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

I hope this helps a bit

I've used Kubuntu and it's pretty much the same as Ubuntu. I know it has a add/remove button. Though it's been awhile since I used Kubuntu. I'm not completely sure but I know I've used something like the on Ubuntu has.

PS I like the older version of gimp better then the new version. I don't like having to know the size of a picture before opening a window of that size.

---

