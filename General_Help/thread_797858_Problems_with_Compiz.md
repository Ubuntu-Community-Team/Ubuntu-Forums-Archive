---
title: "Problems with Compiz"
date: 2008-05-17
forum: General Help
---

### Post by joelr on 2008-05-17
Hi

I wanna use Compiz to customize my desktop, but I cant make it run. This is what happens when I type "compiz" in the terminal:

maja@maja:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA controller])
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
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

My computer is a HP dv6203 (6200-series).

I'm not a killer on this one so please help me.

---

### Post by joshuachad on 2008-05-17
try reading your own error. Its basically telling you exactly what to do.

---

### Post by joelr on 2008-05-17
As I said. Im a beginner.

Anyway.

Checking for nVidia: not present 

and

Checking for Xgl: not present.
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

must be it then. But still I don't how a clue what it means.

Thanks.

---

### Post by rich257 on 2008-05-17
Most likely you'll need to do:
```

$ compiz --replace

```

Would you expect nVidia to be present?  What video card to you have?

---

