---
title: "Compiz Fusion Composite problem"
date: 2008-05-03
forum: General Help
---

### Post by vanmortel on 2008-05-03
Hi,

I just installed Hardy Heron (8.04 LTS Desktop) and I'm having probleme with compiz Fusion. (Intel E8400 + nVidia 8800GT)

When I start compiz, here is the error :

```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0611 (rev a2) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
aborting and using fallback: /usr/bin/metacity

```

So obviously my problem is the X Composite extension. I added this in my Xorg.conf :
```

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

But I kept having the same error that the Composite extension is not present even if my Xorg.log show me this :

```
(**) Extension "Composite" is enabled
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled
```

So help me out here please?
Thanks all!

---

### Post by vanmortel on 2008-05-05
Ok, simple.

Xinerama is not working with Composite at this point so I enabled TwinView and everything worked like a charm.

Enjoy

---

