---
title: "Compiz started with completly white screen"
date: 2008-05-06
forum: General Help
---

### Post by zlochko on 2008-05-06
Hi... I believe that I have successfully started compiz fusion under 8.04 with ATI card (upgraded from 7.10). As from what I understand I get some minor messages in the console, but compiz gives me completely white screen and then everything falls back to metacity after a minute or so...

This is the output:
```
gjokopargo@rd3:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5657 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
```

Does anyone have an explanation for this?

---

### Post by Saint Angeles on 2008-05-06
the white screen means you arent getting direct rendering with your driver.

try this:
[http://ubuntuforums.org/showpost.php?p=4749740&postcount=12](http://ubuntuforums.org/showpost.php?p=4749740&postcount=12)

if the latest fglrx doesn't work, try an older one.

---

