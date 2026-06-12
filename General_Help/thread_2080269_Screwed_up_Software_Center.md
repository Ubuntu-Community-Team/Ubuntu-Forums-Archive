---
title: "Screwed up Software Center"
date: 2012-11-03
forum: General Help
---

### Post by Skifu on 2012-11-03
With no luck in uninstalling oracle java from my laptop, I used brute force and opened up nautilus as root and removed some files with "java" in their name  :oops:
... not the best idea yea I know, but according to "java -version"  its not on my system anymore, so thats good...


So now the Software Center wont start, some wrong files apparently got deleted in the progress.
Tried to re-install u.s.c. using this command

>  sudo apt-get --purge --reinstall install software-centerSoftware center reinstalled correctly, but it still wont start


also tried this guide

[http://coronadora.livejournal.com/82882.html](http://coronadora.livejournal.com/82882.html)

but with no luck



This is what i get when running "software-center" in console:

> (software-center:10776): Gtk-WARNING **: Theme parsing error: gtk.css:227:31: Failed to import: Error opening file: No such file or directory

** (software-center:10776): WARNING **: Failed to load shared library 'libwebkitgtk-3.0.so.0' referenced by the typelib: libwebkitgtk-3.0.soso: cannot open shared object file: No such file or directory

** (software-center:10776): WARNING **: Failed to load shared library 'libjavascriptcoregtk-3.0.so.0' referenced by the typelib: libjavascriptcoregtk-3.0.soso: cannot open shared object file: No such file or directory
Traceback (most recent call last):
  File "/usr/bin/software-center", line 131, in <module>
    session = webkit.get_default_session()
  File "/usr/lib/python2.7/dist-packages/gi/types.py", line 43, in function
    return info.invoke(*args, **kwargs)
gi._glib.GError: Could not locate webkit_get_default_session: libjavascriptcoregtk-3.0.soso: cannot open shared object file: No such file or directoryIs there a way to fix this? What is this webkit libjava hooba hooba thingy? :confused:
Still quite new to linux, and i'm loving it. Only problems I&#8217;ve had so far is of my own stupidity :D

---

### Post by mzrk7 on 2012-11-03
I would try to reinstall software center and java from synaptic. I hope it helps.

---

### Post by Skifu on 2012-11-03
Thank you for your reply, sorry i forgot to mention;
after reinstalling software center via the console, i installed openjdk 7 as well, but software center still won't open

> java version "1.7.0_09"
OpenJDK Runtime Environment (IcedTea7 2.3.3) (7u9-2.3.3-0ubuntu1~12.04.1)
OpenJDK 64-Bit Server VM (build 23.2-b09, mixed mode)idk if that matters

According to synaptic, the file that software center says is missing, is actually installed?
[http://i.imgur.com/M6IAy.png](http://i.imgur.com/M6IAy.png)

---

### Post by techvish81 on 2012-11-04
you can try 'fix broken packages ' from synaptic.

---

### Post by AlexDudko on 2012-11-04
Removing Software Centre's cache could help as well:
> rm -r .cache/software-center

---

### Post by oldos2er on 2012-11-04
It would help to know exactly which files were deleted. No package manager front-end is dependent on java.

---

### Post by sandyd on 2012-11-04
> **Skifu said:**
> With no luck in uninstalling oracle java from my laptop, I used brute force and opened up nautilus as root and removed some files with "java" in their name  :oops:
... not the best idea yea I know, but according to "java -version"  its not on my system anymore, so thats good...


So now the Software Center wont start, some wrong files apparently got deleted in the progress.
Tried to re-install u.s.c. using this command

Software center reinstalled correctly, but it still wont start


also tried this guide

[http://coronadora.livejournal.com/82882.html](http://coronadora.livejournal.com/82882.html)

but with no luck



This is what i get when running "software-center" in console:

Is there a way to fix this? What is this webkit libjava hooba hooba thingy? :confused:
Still quite new to linux, and i'm loving it. Only problems I’ve had so far is of my own stupidity :D

Try
```

sudo apt-get install --reinstall  libwebkitgtk-3.0-0

```

Might end up spouting a few more errors off (missing libraries, .etc .etc)

---

### Post by Skifu on 2012-11-04
Thank you for the replies, but so far nothing helped.
And I have no memory of what files I removed, I didn't even send them to trash, I deleted them entirely :lol:

Oh well, I’ve been meaning to remove windows entirely from my dual-boot laptop quite a while now, so I just decided to back up my important files and make a fresh install & using the entire hard drive.

Good reminder not to mess around as root if you're not 110% sure what you're doing.
Luckily I didn't cause any serious damage that would have resulted in loss of more important folders.

So remember folks, don't be as careless as me! ;-)

---

