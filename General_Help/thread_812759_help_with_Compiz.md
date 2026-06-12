---
title: "help with Compiz"
date: 2008-05-30
forum: General Help
---

### Post by kystorms on 2008-05-30
I tried to get Compiz running today, * have had it running on this same machine before Hardy, worked fine*
and when I typed compiz --replace in the terminal this is what i got back:

lisac@lisac-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5159 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

Would anyone be willing to explain to this newb what this means, and what I need to do to correct it, so that compiz will run?

thank you
:)

---

### Post by Forlong on 2008-05-30
According to the output, Compiz is in fact running.

As for the error message: that's because of a [bug]("https://bugs.launchpad.net/bugs/209207") in Hardy.
Run ```
gconftool-2 -s -t string /apps/compiz/plugins/scale/allscreens/options/initiate_edge Disabled
``` in a terminal to fix it.

---

### Post by kystorms on 2008-05-31
wow, that worked awesome , thank you so much. Also checked out your other help pages on your blog, you ROCK!
:KS

---

