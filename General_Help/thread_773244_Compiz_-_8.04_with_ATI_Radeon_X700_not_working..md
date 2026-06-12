---
title: "Compiz - 8.04 with ATI Radeon X700 not working."
date: 2008-04-28
forum: General Help
---

### Post by rekster on 2008-04-28
Hello,

I am trying out the latest Ubuntu on my Acer Ferrari 4000 notebook.  (has an ATI Radeon X700).

Would like to get Compiz running as I had no luck on prior releases of Ubuntu and ended up messing things up more than anything lol.

In any case, I have done the following:

- enabled the Restricted ATI driver
- enabled the Advanced Desktop Effects Settings
- enabled the Desktop Cube and made sure I had 4 workspaces enabled

Problem:  Nothing happens.

Tried starting up compiz manually and this is the message I get:

$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5653 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
^[	^[	GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.


I also used EnvyNG in case drivers were not up to date and same problem.

Any help would be much appreciated, I'm getting frustrated again as I was the last time I tried to get this all set up.

Thanks!

---

### Post by rekster on 2008-04-28
I just enabled the rotate cube option and that seems to work neat, my whole desktop rotates to the next workspace, so Compiz MUST be functioning.  Just cant see a cube ever if that helps pinpoint anything?

Cheers.


Edit:  Never mind, I guess I just didn't understand how it worked, if I ctrl-alt-click i do get a rotateable cube.  I assumed that I could activate and flip the cube around by Ctrl-Alt-(Arrows)

Sorry to make you read this for nothing.. 

Cheers.

---

