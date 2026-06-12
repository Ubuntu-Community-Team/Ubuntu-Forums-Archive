---
title: "Help fix my system!"
date: 2007-10-28
forum: General Help
---

### Post by pizzy on 2007-10-28
Hi,
I'm having problems.  When I start some applications I get the following error

```
 gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk
  File "/usr/bin/software-properties-gtk", line 29, in <module>
    import gtk.glade
ImportError: No module named glade

```

I've tried but can't fix this... so I want to know if there is a way to re-sync all my packages with the ones in the Ubuntu repo?  I think I must have installed something that has broken things...

Thanks

---

### Post by Stemp on 2007-10-28
Is package python-glade2 installed ?

---

### Post by pizzy on 2007-10-28
yes, and I've reinstalled it to make sure!!  strange?

sudo apt-get install python-glade2
[sudo] password for user
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-glade2 is already the newest version.

---

### Post by Stemp on 2007-10-28
Yes strange !

Ok here is the list of my installed packages with glade : 

```
i A glade-3                         - GTK+ 2 User Interface Builder             
i A glade-gnome-3                   - GTK+ 2 User Interface Builder (with GNOME 
i   libglade2-0                     - library to load .glade files at runtime   
iBA libglade2-dev                   - development files for libglade            
i   libglade2.0-cil                 - CLI binding for the Glade libraries 2.6   
i A libgladeui-1-7                  - GTK+ User Interface Build core library    
i A libgladeui-1-common             - GTK+ User Interface Build core library    
i   python-glade2                   - GTK+ bindings: Glade support              

```

---

### Post by pizzy on 2007-10-28
thanks, I've got these all installed now, was missing a couple, but still same error!!

/usr/bin/gnome-app-install
Traceback (most recent call last):
  File "/usr/bin/gnome-app-install", line 30, in <module>
    main()
  File "/usr/lib/python2.5/site-packages/AppInstall/activation.py", line 435, in main
    from AppInstall import AppInstall
  File "/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py", line 31, in <module>
    import gtk.glade
ImportError: No module named glade


Thanks for your help!

---

### Post by Stemp on 2007-10-28
I'm sorry but I have no ideas of what is going wrong :(

probably an environment path problem, but I don't know much python.

---

### Post by aksommerville on 2007-10-29
I'm having the same problem. Python glade apps worked fine (w/ python 2.5.1 and Gutsy) until just yesterday. I'm not sure at exactly what point they started failing, but it was while I was trying to install GCompris development libraries.

Maybe this helps?--

andy@andy-laptop:~$ python
Python 2.5.1 (r251:54863, Oct  5 2007, 13:36:32) 
[GCC 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import gtk
>>> import gtk.glade
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named glade

---

### Post by pizzy on 2007-10-29
Hey, if you get a fix could you post it?  Thanks!

---

