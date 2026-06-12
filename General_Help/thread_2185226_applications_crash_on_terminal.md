---
title: "applications crash on terminal"
date: 2013-11-01
forum: General Help
---

### Post by acorreia on 2013-11-01
I'm well used to call some applications via terminal, and that's really important for my research. I'm having trouble starting some applications via terminal, and I don't know how to find what's wrong. The applications work well when I click on them, but not if I try to launch them via terminal. 

Some details (what else should I cite here?): distro ubuntu 12.04 LTS 64bit Dell Inspiron laptop

Examples:
```

$ gedit
(gedit:5531): GLib-ERROR **: creating thread 'dconf worker': Error creating thread: Resource temporarily unavailable
Trace/breakpoint trap (core dumped)

```

```

$ firefox
Segmentation fault (core dumped)

```

```

$ idl
IDL Version 7.1.1 (linux x86_64 m64). (c) 2009, ITT Visual Information Solutions
% Internal threading error: Unable to create thread (IDL_ThreadCreate()
   calling pthread_create()).
  Resource temporarily unavailable

```

Can someone please point me in the direction on how to find out what's wrong with my terminal? All these applications used to run fine in the terminal, and they still run ok when clicking, but not if I try to start them 'by hand'. Any clue? I'm afraid something might have broken after an upgrade...

Cheers

---

### Post by jamesisin on 2013-11-01
Are you logged into the terminal as the same user who is logged into the GUI?

---

### Post by kbogert2 on 2014-05-25
I had this same problem after moving my home directory from a 32 bit to a 64 bit machine.  It turns out the cause was I had a ulimit set in my .bashrc file:

ulimit -s 4000000000

Not sure why I had that in there, but removing it caused the error to go away.  I saw it most often with python gnome applications, and all you had to do was import gtk to cause the error:

$ python
Python 2.7.3 (default, Feb 27 2014, 19:58:35) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import gtk


(.:7185): GLib-ERROR **: creating thread 'dconf worker': Error creating thread: Resource temporarily unavailable
Trace/breakpoint trap

---

### Post by acorreia on 2014-08-04
Thank you so much kbogert2!!! You nailed it!
I had the same ulimit setting in my .bashrc, don't know why either. I just commented it out, restarted the terminal, and everything worked!!

:p

---

### Post by Bucky Ball on 2014-08-04
Good news. To help others, please mark the thread as solved by following the second link in my signature. ;)

---

