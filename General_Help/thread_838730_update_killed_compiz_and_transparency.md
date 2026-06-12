---
title: "update killed compiz and transparency"
date: 2008-06-23
forum: General Help
---

### Post by jasonpeinko on 2008-06-23
I updated and then restarted and compiz does not work anymore.

```

jason@jason:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 05:00.0 0300: 10de:0427 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Killed


```

edit: it appears another reboot fixed it.

---

### Post by sledhead45 on 2008-06-27
Same story here.. Compiz worked like a charm until i applied the latest updates. I've tried restarting a couple times. Let me know if any more info is needed. thanks..

```
travis@ubuntu:~$ compiz --replace
Checking for Xgl: not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity 
/usr/share/themes/Human/gtk-2.0/gtkrc:211: Invalid symbolic color 'selected_bg_color'
/usr/share/themes/Human/gtk-2.0/gtkrc:211: error: invalid identifier `selected_bg_color', expected valid identifier

```

```
travis@ubuntu:~$ uname -a
Linux ubuntu 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

```

```
travis@ubuntu:~$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] [1002:4c57]
travis@ubuntu:~$ 

```

---

### Post by sledhead45 on 2008-06-27
here's a little more info if it helps 

> travis@ubuntu:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 


---

### Post by Mateus18 on 2008-06-27
can you help me? (or somebody, please)
i receive de cd, install an all work excellent.
than i download de compiz.bdo and shows a window compiz manager, but i try too reinstal, and nothing hapend...
what i have to do?

---

### Post by sledhead45 on 2008-06-27
It appears the place to start these days for getting compiz working is try the instructions to install and run [compiz-check]("http://forlong.blogage.de/article/pages/Compiz-Check") . 
If those tests pass successfully go to system > preferences > appearance > visual effects tab and select extra. 
If some of those checks fail use google and these forums to locate an answer. Good luck.

As for my previous problem, I inadvertently dorked up my libgl.so.1 link. all is fine again..
thanks

---

