---
title: "Another &quot;Desktop effects could not be enabled&quot;"
date: 2008-05-17
forum: General Help
---

### Post by capleton on 2008-05-17
I'm getting a "Desktop effects could not be enabled"  when I try to adjust the Visual Effects tab in Appearence Preferences.  this is what I get in the terminal with command 'compiz'
I installed Xgl and rebooted, but that didn't work either (although it did recognize Xgl in the terminal).  I also tried re-installing Compiz and dependencies.  I've uninstalled Xgl.  This is what I get right now w/ compiz in terminal```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:7145 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (4096): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

Any ideas?

---

### Post by macaholic on 2008-05-17
What kind of graphics card do you have?

---

### Post by capleton on 2008-05-17
it's an ati x1400

And I'm running ATI driver glrx

---

### Post by capleton on 2008-05-18
bump

---

### Post by tommyhakinen on 2008-05-18
I guess your Graphic Card is blacklisted.
> [http://ubuntuforums.org/showthread.php?t=765875](http://ubuntuforums.org/showthread.php?t=765875)

---

### Post by capleton on 2008-05-18
Are you sure?  I don't get that exact output in the terminal; and it had been working for several weeks after I first installed Hardy

---

### Post by capleton on 2008-05-18
Okay, here's one... in the terminal **compiz --replace** fails to enable compiz, output is same as in first post.  *Then* (out of sheer frustration) I typed **compiz --renew**, the screen flashes,  and it works!?!  This is the output:  ```
compiz --renew
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:7145 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (4096): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: Unknown option '--renew'

/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```

Here's the kicker, when I disable compiz and try 'compiz --replace' then 'compiz' or any combination or succession of these commands in the terminal, it doesn't work... but doing **'compiz --replace' then 'compiz --renew' has worked three times**. so... WTF ?

Finally, how can I fix the last two lines: {/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format} and {GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.}  I can't find the directory

(should I start a new thread?)

---

### Post by capleton on 2008-05-18
Buhuhuhuhuhnmp

---

### Post by Forlong on 2008-05-19
[http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

