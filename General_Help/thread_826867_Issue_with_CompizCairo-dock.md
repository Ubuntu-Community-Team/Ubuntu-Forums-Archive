---
title: "Issue with Compiz/Cairo-dock"
date: 2008-06-12
forum: General Help
---

### Post by djmoore85 on 2008-06-12
Alright, I installed cairo-dock and it works great, just a couple minor complaints. The black border or box that is around it, how do I get rid of it and make that transparent? Also, when I run compiz in terminal, I get this output: 

```
root@Daniel-7:/home/daniel# compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:05.0 0300: 1002:5955 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Couldn't find a perfect decorator match; trying all decorators
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

Any suggestions on getting all this stuff working properly? Thanks in advance, by the way my graphics controller is ATI Radeon Xpress 200M

---

### Post by Houli on 2008-06-12
Try this

```
sudo apt-get install xserver-xgl
```

Tell me if it works then.

---

### Post by djmoore85 on 2008-06-12
Now I get this on output:

```
 compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:05.0 0300: 1002:5955 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
```

---

### Post by Houli on 2008-06-12
Sorry mate haven't got a clue.

---

### Post by djmoore85 on 2008-06-12
Rebooted, tried again and got:

```
root@Daniel-7:/home/daniel# compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Couldn't find a perfect decorator match; trying all decorators
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

---

### Post by IanW on 2008-06-12
As an alternative to Compiz, Cairo-Dock will also work with xcompmgr from the repositories.

---

### Post by djmoore85 on 2008-06-12
Ok I purged compiz from my computer, installed xcompmgr, but when I run in terminal I just get a hang up and the blinking cursor continuously

---

### Post by psyopper on 2008-06-14
Try running Compiz Check to see what's wrong with starting/running compiz.

[http://forlong.blogage.de/article/pages/Compiz-Check]("http://forlong.blogage.de/article/pages/Compiz-Check")

---

### Post by fabounet on 2008-06-16
there is the support for fake transparency in Cairo-Dock 1.6.0 (cairo-dock -F), even if I would suggest to try xcompmgr first. ;-)

---

