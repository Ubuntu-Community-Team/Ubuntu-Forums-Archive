---
title: "Compiz errors"
date: 2008-05-26
forum: General Help
---

### Post by sofasurfer on 2008-05-26
Installed Compiz on Hardy with Synaptic.
I opened terminal and typed "compiz". This is my output...

daryl@ubuntu:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 10de:01d3 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

Can anyone please help my decipher this problem?

---

### Post by el-mar01 on 2008-05-26
Post the output of Compiz-Check ... [http://forlong.blogage.de/article/pages/Compiz-Check](http://forlong.blogage.de/article/pages/Compiz-Check)

---

### Post by sofasurfer on 2008-05-26
daryl@ubuntu:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G72 [GeForce 7300 SE] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

---

### Post by Forlong on 2008-05-26
> /usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
This is not an error but a warning you can safely ignore.
> GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
That's because of a [bug]("https://bugs.launchpad.net/bugs/209207") in Hardy.
Run ```
gconftool-2 -s -t string /apps/compiz/plugins/scale/allscreens/options/initiate_edge Disabled
``` in a terminal to fix it.

---

### Post by sofasurfer on 2008-05-26
I did what you said Forlong. Now compiz-check shows...

daryl@ubuntu:~$ compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G72 [GeForce 7300 SE] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Xgl

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [SKIP]
 Checking for non power of two support...          [SKIP]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems.../usr/bin/compiz-check: line 616: [: : integer expression expected
           [ OK ]


If I just run Compiz I get...

daryl@ubuntu:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


This is as far as it goes. Nothing happens after this.

---

### Post by Forlong on 2008-05-26
> **sofasurfer said:**
> I did what you said Forlong.
Erm... yeah, but you also installed Xgl in the meantime.
You don't need that on a Nvidia card, remove it:
```
sudo apt-get remove xserver-xgl
```
Afterwards, restart X  and try again.

---

### Post by sofasurfer on 2008-05-26
I removed Xgl. I never learned what it means to "restart X" so I restarted the computer. Now when I run Compiz I get this...

daryl@ubuntu:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 10de:01d3 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

---

### Post by Forlong on 2008-05-26
Great. Now Compiz should be running.

And you restart your X server by pressing [Strg]+[Alt]+[Backspace] at the same time.

edit: does Compiz-Check still give you that error message?

---

