---
title: ":( Compiz Fusion not working"
date: 2008-05-04
forum: General Help
---

### Post by mardigraw on 2008-05-04
it stopped working a while back when I updated, and now when i try to replace i get this 

rahbi@rahbicomp:~$ sudo compiz replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 05:00.0 0300: 10de:0400 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'replace'
/usr/bin/compiz.real (core) - Warn: Plugin 'core' already active
Couldn't find a perfect decorator match; trying all decorators
Found no decorator to start
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
*** glibc detected *** /usr/bin/compiz.real: corrupted double-linked list: 0x00000000007b42e0 ***
i really want this fixed and its
something about my decorator or my xgl is wrong, i dont know alot about this stuff so try and keep it simple pls

---

### Post by overdrank on 2008-05-04
> **mardigraw said:**
> it stopped working a while back when I updated, and now when i try to replace i get this 

rahbi@rahbicomp:~$ sudo compiz replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 05:00.0 0300: 10de:0400 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'replace'
/usr/bin/compiz.real (core) - Warn: Plugin 'core' already active
Couldn't find a perfect decorator match; trying all decorators
Found no decorator to start
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
*** glibc detected *** /usr/bin/compiz.real: corrupted double-linked list: 0x00000000007b42e0 ***
i really want this fixed and its
something about my decorator or my xgl is wrong, i dont know alot about this stuff so try and keep it simple pls

Hi and what is the model of graphics card and what version of Ubuntu are you using?

---

### Post by mardigraw on 2008-05-04
im using ubuntu hardy heron the newest release, and my graphics card is a geforce 8600 gt 512 mb  i forgot the manufacturer

---

### Post by Zorael on 2008-05-04
Make it 'compiz --replace' instead, without sudo.
```
$ compiz --replace &
```

It also complained about there not being any window decorators available, so first off, you might want to grab the **emerald** package.
```
$ sudo aptitude install emerald
```

---

### Post by mardigraw on 2008-05-05
still cant use cube for some reason :(

---

### Post by macaholic on 2008-05-05
> **mardigraw said:**
> still cant use cube for some reason :(
Is it enabled in CCSM? You will have to enable the custom effects to check.

---

