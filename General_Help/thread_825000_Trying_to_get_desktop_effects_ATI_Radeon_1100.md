---
title: "Trying to get desktop effects ATI Radeon 1100"
date: 2008-06-10
forum: General Help
---

### Post by lorgonjortle on 2008-06-10
I have an ATI Radeon 1100 Xpress. The compiz check said everything was ok. Yet, this isn't working. What do I have to do to get desktop effects? I already have the advanced desktop effects manager installed. But nothing works. Thanks for any help. And I'll post any log or what not. Here is a pic that might help:
[img]http://www.jettmedia.com/files/makl4mi4kck6z8n2z7dn.png[/img]

---

### Post by Forlong on 2008-06-10
What's the output when running ```
compiz
``` in a terminal now that you reset your xorg.conf?

---

### Post by lorgonjortle on 2008-06-10
```

Checking for Xgl: not present. 
Found laptop using ati driver. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x3c00005 specified for 0x3c0003b (Dev-C++ 4.).
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x3c00005 specified for 0x3c0003b (Dev-C++ 4.).
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x3c00005 specified for 0x3c0003b (Dev-C++ 4.).


```

---

### Post by Forlong on 2008-06-10
Try enabling the "ATI accelerated graphics driver"

---

### Post by lorgonjortle on 2008-06-10
Oh my god! It worked! I have tried this many times before... what changed it now to make it work? Do you know? Thanks so much!

---

### Post by lorgonjortle on 2008-06-10
Ran into a probelem though.... None of the effects work... I enable them, but it doesn't do anything. Here is the link to the new post about getting the effects to work. Thanks!
[http://ubuntuforums.org/showthread.php?p=5158823#post5158823](http://ubuntuforums.org/showthread.php?p=5158823#post5158823)

---

