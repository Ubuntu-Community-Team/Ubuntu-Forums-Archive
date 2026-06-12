---
title: "Python applications don't work.."
date: 2008-04-11
forum: General Help
---

### Post by the_penguin_pwnz on 2008-04-11
Good morning everyone.

I have a problem with python-based applications, they don't work anymore.
For example, emesene and  screenlets, they used to work like magic, but now they don't even start.

I think the problem is that a couple of days ago, I tried to install Python 3.0 Alpha.
But now I got it back to Python2.5.

I tried to start these applications from the terminal, but I got the following python error message.

```
Traceback (most recent call last):
  File "/usr/share/emesene/Controller.py", line 21, in <module>
    import gtk
ImportError: No module named gtk

```

I tried to install python-gtk2, and pygtk..etc. But everything seems to be installed already.

Please help. :)

---

### Post by ibutho on 2008-04-11
The problem seems to be with python-gtk2. Did you actually reinstall it?

---

### Post by the_penguin_pwnz on 2008-04-11
I'm not sure.

I think I did yeah.
Can you help me fix it?

---

### Post by ibutho on 2008-04-11
Try the following,
```
aptitude reinstall python-gtk2
```

---

### Post by the_penguin_pwnz on 2008-04-11
Didn't solve the problem. :(

I think I don't have pygtk installed on my machine.
I tried to install it, but when I tried to use the ' sudo ./configure ' command, it gave me the following output:

```

.
.
.
checking for GLIB - version >= 2.8.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error: gobject is required to build pygtk?

```

I'm not sure what to do..

---

### Post by ibutho on 2008-04-11
python-gtk2 is the same as pygtk2, so thats the package you need to install/reinstall using the Ubuntu packaging tools. It could be that installing Python 3 messed up your Ubuntu Python 2.x packages, so its also worth trying 
```
sudo aptitude reinstall '~n python'
```
That should reinstall all the python packages already installed on your system.

---

### Post by the_penguin_pwnz on 2008-04-11
Still, nothing seems to have changed.. ><

---

### Post by GTengineer on 2008-04-11
I am having a similar problem.....
[http://ubuntuforums.org/showthread.php?t=751791](http://ubuntuforums.org/showthread.php?t=751791)

but no matter what I do even reinstalling it nothing seems to fix python :confused:

---

### Post by the_penguin_pwnz on 2008-04-11
This is very strange.. ><

---

### Post by the_penguin_pwnz on 2008-04-11
I don't know.

Personally I'm starting to consider reinstalling the entire O.S..

But I think I'll just wait 'till Hardy Heron finally comes out.

---

### Post by little_penguin on 2008-04-26
I had this problem for quite a while, and solved it in the end by following the advice in this thread, specifically post #37:

[http://ubuntuforums.org/showthread.php?t=123415&highlight=no+module+named+gtk&page=4]("http://ubuntuforums.org/showthread.php?t=123415&highlight=no+module+named+gtk&page=4")[http://ubuntuforums.org/showthread.php?t=123415&highlight=no+module+named+gtk&page=4](http://ubuntuforums.org/showthread.php?t=123415&highlight=no+module+named+gtk&page=4)

Hope it works for you too.

---

