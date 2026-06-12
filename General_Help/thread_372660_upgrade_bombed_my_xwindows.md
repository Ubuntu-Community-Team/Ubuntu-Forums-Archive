---
title: "upgrade bombed my xwindows"
date: 2007-02-28
forum: General Help
---

### Post by Entity` on 2007-02-28
After a very long night of upgrading from Ubuntu 5.10 to 6.06, I rebooted my server and guess what happened.  I got an error message saying that xwindows could not load due to some sort of problem.  Right now I can't give the exact output but what I do remember it that the log told me that there is no moniter present.  Thats kind of an Oxy Moron right there, as I can see the error on my moniter, and that the error tells me that there is no moniter present.  I am not about to give up 12 hours of upgrading right there.

Can someone help me.  Exact output will come later when I can get home and view it.
Thanks in advance.

---

### Post by an.echte.trilingue on 2007-02-28
That is your video card.

The command you need is most likely ```
sudo dpkg-reconfigure -phigh xserver-xorg
```  That will start a video card config wizard of sorts.  If you have problems figuring what the input should be drop us a line and let us know.  You mlight need to download a new video driver.

Take care
-mat

---

### Post by Entity` on 2007-02-28
Again thanks for the help, but as promised I will give the output anyway; just in case.

Basic output
```
(EE) Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(EE) Failed to load "GLcore" (loader failed, 7)
(EE) Failed to load "nvidia" (module does not exist, 0)
(EE) No drivers available
```

Advanced output
```
(WW) The directory "/usr/share/x11/fonts/cyrillic" does not exist.
                               Entry deleted from font path.
(WW) the directory "usr/share/X11/fonts/CID" does not exist.
                               Entry deleted from font path.
(WW) 'fonts.dir' not found (or not valid) in
         "var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
                               Entry deleted from font path.
         (Run 'mkfontdir' on
         "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
```

later on;
```
(EE) Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(EE) Failed to load "GLcore" (loader failed, 7)
```

then farther down;
```
(WW) Warning, couldn't open module nvidia
(EE) Failed to load "nvidia" (module does not exist, 0)
(EE) No drivers available
```

There, all done.

---

### Post by hikaricore on 2007-02-28
By upgrading to Dapper you basicly made your old nvidia driver useless.  But fear not this is easy to resolve.

You'll need to either [manually]("http://www.nvidia.com/object/unix.html") or use a script like [envy]("http://albertomilone.com/nvidia_scripts1.html") to reinstall your video drivers for the new kernel.

Heres a few links if you need more info:
[http://www.ubuntuforums.org/showthread.php?t=301499&highlight=howto+nvidia+driver](http://www.ubuntuforums.org/showthread.php?t=301499&highlight=howto+nvidia+driver)
[http://www.ubuntuforums.org/showthread.php?t=336412&highlight=howto+nvidia+driver](http://www.ubuntuforums.org/showthread.php?t=336412&highlight=howto+nvidia+driver)

---

