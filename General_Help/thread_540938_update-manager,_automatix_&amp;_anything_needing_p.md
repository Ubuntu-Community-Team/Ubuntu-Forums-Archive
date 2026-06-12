---
title: "update-manager, automatix &amp; anything needing python gtk broken [Solved]"
date: 2007-09-02
forum: General Help
---

### Post by npc100 on 2007-09-02
Hi All,

hoping someone can help with a rather frustrating problem. Whenever I try and run update-manager, automatix, or anything else that requires the python gtk libs, I get the following error:

```

neil@neil-desktop:~$ update-manager
/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:48: RuntimeWarning: tp_compare didn't return -1 or -2 for exception
  from gtk import _gtk
ImportError: could not import atk
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 29, in <module>
    import gtk.glade
ImportError: cannot import name Widget from gtk

```

I've reinstalled all the gtk libs and the python-gtk libs, but no joy.

I can see a few other people have posted the same problem, but it doesn't look as though any solution has been found.

Any ideas where I should start?

Many thanks, Neil

---

### Post by npc100 on 2007-09-06
*bump*

Anyone? I've seen the error (or something very similar) reported quite a few times on various forums, but no one has ever replied.

I've reinstalled gnome, python, python-gtk2, and just about every other related lib (including all the dev ones) but still no joy :(

Any help really appreciated - I am at a complete loss as to where to look next. Can't even get into my restricted-drivers manager :confused:

---

### Post by npc100 on 2007-09-08
After much digging around, and many wasted hours, I finally worked it out :)

Reinstalling libatk with a

```
 sudo apt-get install --reinstall libatk1.0-0 
```

resolved the problem :)

---

### Post by kqueenc on 2007-09-29
I have the same problem but no use after tried out reinstall libatk1.0-0.
Finally resolved by uninstall atk1.9.1 while I compiled and installed couple days ago.
:):)
But still thanks for the hint or I might never know which library is going wrong.

---

### Post by rahul_bhise on 2008-01-04
i have also the same error
```
**brahul@uhome:~$ update-manager**
/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:48: RuntimeWarning: tp_compare didn't return -1 or -2 for exception
  from gtk import _gtk
ImportError: could not import atk
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 29, in <module>
    import gtk.glade
ImportError: cannot import name Widget from gtk
**brahul@uhome:~$ sudo apt-get install --reinstall libatk1.0-0**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/79.1kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 149054 files and directories currently installed.)
Preparing to replace libatk1.0-0 1.20.0-0ubuntu1 (using .../libatk1.0-0_1.20.0-0ubuntu1_i386.deb) ...
Unpacking replacement libatk1.0-0 ...
Setting up libatk1.0-0 (1.20.0-0ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
brahul@uhome:~$
```
but still the problem is not resolved

---

### Post by rahul_bhise on 2008-01-06
problem solved
i installed some software
libiconv-1.11
glib-2.14.3
atk-1.9.1
and my update-manager, yelp and all the system>administration>*all application*  started working properly

---

### Post by Stu09 on 2008-04-26
I'm getting this error. The packages in the previous posts don't seem to be available anymore
```

stuart@MacBook:~$ update-manager
/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:48: RuntimeWarning: tp_compare didn't return -1 or -2 for exception
  from gtk import _gtk
ImportError: could not import atk
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 29, in <module>
    import gtk.glade
ImportError: cannot import name Widget from gtk

```

---

