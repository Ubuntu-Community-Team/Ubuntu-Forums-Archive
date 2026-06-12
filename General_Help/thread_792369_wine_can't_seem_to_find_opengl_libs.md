---
title: "wine can't seem to find opengl libs"
date: 2008-05-12
forum: General Help
---

### Post by Anhaedra on 2008-05-12
Hey all, I just installed Ubuntu on my old pile, I have my nVidia drivers installed, OpenGL works, just not in wine.

SPECS
---------------
1.42ghz AMD Sempron Socket 462
512MB DDR 400
crap PC Chips motherboard
nVidia Geforce 4 MX420

Ubuntu 8.04 with compiz enabled
Wine 1.0-rc1

----------------

Whenever I try to run a game using wine, this is what I get.

```
fixme:win:EnumDisplayDevicesW ((null),0,0x32f784,0x00000000), stub!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
err:wgl:is_extension_supported No OpenGL extensions found, check if your OpenGL setup is correct!
fixme:winmm:MMDRV_Exit Closing while ll-driver open
```


I know that OpenGL is not broken because my screensavers work fine, I get some 870fps in GLXGears, and Nexuiz will run.

---

