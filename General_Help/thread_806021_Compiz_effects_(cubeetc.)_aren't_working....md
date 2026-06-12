---
title: "Compiz effects (cube/etc.) aren't working..."
date: 2008-05-24
forum: General Help
---

### Post by Th3Professor on 2008-05-24
How do I get them working again?

Everything is set up fine in "advanced desktop settings" and "system>preferences>appearance" is set to "extra" in "visual effects".

It looks like something happened that caused the compiz features (at least the cube-type features) to crash.

Is there a command I can run to restart it?

Thanks!

EDIT:
The "compiz-" type commands don't do it. It's on the tip of my tongue, I remember doing this before... just forgot what the command was.

---

### Post by Zoja on 2008-05-24
This is a step-by-step tutorial on how to do magic with compiz-fusion : 
[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

i think you probably have 2 virtual desktops instead of 4 and that way the cube won't startaaa ;)

---

### Post by Tobi-fp on 2008-05-24
> **Th3Professor said:**
> How do I get them working again?

Everything is set up fine in "advanced desktop settings" and "system>preferences>appearance" is set to "extra" in "visual effects".

It looks like something happened that caused the compiz features (at least the cube-type features) to crash.

Is there a command I can run to restart it?

Thanks!

EDIT:
The "compiz-" type commands don't do it. It's on the tip of my tongue, I remember doing this before... just forgot what the command was.



Hey there..
Try running a terminal and write "compiz --replace", then afterwards if it crashes, copy/paste the outcome of the terminal here.

Il be happy to help.

---

### Post by Th3Professor on 2008-05-24
> **Zoja said:**
> This is a step-by-step tutorial on how to do magic with compiz-fusion : 
[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

i think you probably have 2 virtual desktops instead of 4 and that way the cube won't startaaa ;)

Nope... I have 4 workspaces.

However, when the cube stuff (and similar fancy features) initially vanished on me, it automatically put me back down to 2 workspaces. Don't know why. Though I immediately put it back to 4.

I was curious about the cube w/ 2 workspaces, it actually does work... kinda cheesy though...

...in any case,  I'm just hoping to get the fancy "fusion" etc. stuff back.

> **Tobi-fp said:**
> Hey there..
Try running a terminal and write "compiz --replace", then afterwards if it crashes, copy/paste the outcome of the terminal here.

Il be happy to help.

Here's what it read back to me on the "--replace":
```

$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2a02 (rev 0c) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
```

I thought there was a command other than compiz to get the cube stuff working again... any ideas?

---

### Post by Tobi-fp on 2008-05-26
Hey lad,
Try disabling "snapping windows" if it is turned on

---

### Post by nzadLithium on 2008-05-26
goto settings<<preferences<<advanced desktop effects settings.
Try using that to get everything going.

---

### Post by kaboodle_fish on 2008-05-26
Install the packages fusion-icon and compizconfig-settings-manager from synaptic 

You can then use this to choose your window manager, window decorator and adjust all the advanced settings

---

