---
title: "Compiz is eating my mouse pointer!"
date: 2008-06-14
forum: General Help
---

### Post by mrbucket on 2008-06-14
[IMG]http://magicschoolbus.info/mouse.jpg[/IMG]

When compiz starts in my default install of ubuntu, I get a funky mouse pointer like that. it corrects itself if I move out of the application that has focus, but then once i click it goes back to this. I'm running 8.04, and the proprietary fglrx driver. 

This is on my IBM Thinkpad T60p.

Here's some output:

cable@smashed:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY FireGL V5250
OpenGL version string: 2.1.7412 FireGL Release

cable@smashed:~$ compiz -replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:71d4 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (4096): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: Unknown option '-replace'

/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

Ideas? I tried using SWCursor already but that didn't work. I know it's compiz because if i disable effects, I have no cursor problems.

---

### Post by GrandpaLeaman on 2008-06-15
First, I noticed you have a warning about unknown option '-replace'. The correct syntax is compiz --replace.

Second, you have an unsupported value error.

> GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.I ran into this a few weeks ago. If you go into Configuration Editor and follow the path noted above, you may find that this value has illegal characters in it. Mine were brackets. Just double click on the value field to the right of 'initiate_edge' and put "Disabled" (without the quotes of course) in that field if you want this feature disabled. I have mine set to "TopRight".

Hope this helps!

Oh, I just remembered that there is a Cursor theme field in CCSM. Go to general options, in the general tab. It's about halfway down. Have you changed this option to the cursor you want to use?

---

