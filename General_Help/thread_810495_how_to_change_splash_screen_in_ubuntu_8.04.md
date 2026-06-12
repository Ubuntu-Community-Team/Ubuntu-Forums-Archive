---
title: "how to change splash screen in ubuntu 8.04"
date: 2008-05-28
forum: General Help
---

### Post by damansandhu on 2008-05-28
i am using ubuntu 8.04 and how to change splash screen??

---

### Post by Ohwii on 2008-05-28
Hi 

well first you should install the starup manager either by commandline or via synaptic , but for a detailed guide check [This]("http://web.telia.com/~u88005282/sum/installation.html")

then just download a theme on gnome look

Afterwards just use the startup manager to install the theme 

Cheers

oh wii

---

### Post by svenpikk on 2008-06-13
I installed the startupmanager and it appeared in the System->Administration menu, but when i click on the icon it starts loading and after that does nothing at all, as if it wasn't installed at all...what might be the problem, any help is welcome!!

Sven

---

### Post by Forlong on 2008-06-14
Run ```
startupmanager
``` in a terminal to look for error messages.

---

### Post by Thunderh on 2008-08-26
Hello

I have the same problem as svenpikk. Tried to run the manager from terminal and i got this message:

```

Traceback (most recent call last):
  File "/usr/sbin/startupmanager", line 31, in <module>
    from gtk_frontend import SumGui
  File "/usr/share/startupmanager/gtk_frontend.py", line 31, in <module>
    import gnome.ui
  File "/var/lib/python-support/python2.5/gtk-2.0/gnome/__init__.py", line 13, in <module>
    from _gnome import *
ImportError: /usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf

```

---

### Post by sidewinder46 on 2008-08-29
The easiest way that i have found is with Ubuntu tweak.  Its one of the many features, [Ubuntu Tweak]("http://ubuntu-tweak.com/downloads")  Hopefully this helps.

---

