---
title: "XGL Compiz Error?"
date: 2008-05-28
forum: General Help
---

### Post by sjones411 on 2008-05-28
Howdy, I'm pretty new to Ubuntu and am trying to get compiz running on my new HP TX2000z tablet.  It's got the Nvidia GeForce Go 6150 integrated graphics card with the ram boosted in the bios to 128mb.  I am using the restricted drivers.  When I run Compiz I get this error:

```
stu@stu-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:05.0 0300: 10de:0244 (rev a2) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```

Does anyone have any thoughts?  Here's the output I get from the Compiz-Check script if that's any help:

```
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

---

### Post by FuturePilot on 2008-05-28
Does it not start? I don't see anything in the output there that would show it's not working.

If you mean the XGL error, that's normal. You don't need XGL with Nvidia cards. The GConf Backend error would suggest you have an invalid value set fot the Scale plugin. If you open the CompizConfig Settings Manager (System&#8594;Preferences&#8594;Advanced Desktop Effects Settings) and go under the Scale plugin, make sure you have a valid setting for the Screen edge.

---

### Post by sjones411 on 2008-05-28
> **FuturePilot said:**
> Does it not start? I don't see anything in the output there that would show it's not working.

Oh wow... ><  It did start, and I just didn't realize any of the effects kicked in.  Sorry for the forum spam eveyone ><  Is there a way to delete a post?

---

### Post by Forlong on 2008-05-29
Don't mind, actually it's not that uncommon, that people do not realize Compiz is running. After all, Ubuntu obscures it pretty efficiently ;)

As for those error messages:
> /usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
This is not an error but a warning you can safely ignore.
> GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
That's because of a [bug]("https://bugs.launchpad.net/bugs/209207") in Hardy.
Run ```
gconftool-2 -s -t string /apps/compiz/plugins/scale/allscreens/options/initiate_edge Disabled
``` in a terminal to fix it.

---

