---
title: "XMMS Plugin problems"
date: 2005-05-08
forum: General Help
---

### Post by orion_114 on 2005-05-08
I found a media library plugin for XMMS at the following [site.](http://xpg.dk/blog/projects/xmms-media-library)
I have installed the glib, gtk and xmms dev packages.
When i run ./configure I see this error.
```

.....
checking for XMMS - version >= 1.2.4... no
*** The xmms-config script installed by XMMS could not be found.
*** If XMMS was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the XMMS_CONFIG environment variable to the
*** full path to xmms-config.
.....

```
I found the xmms-config file in /usr/bin/ but when I add this to the Makefile like so: 
XMMS_CONFIG  = /usr/bin/
or
XMMS_CONFIG  = /usr/bin/xmms-config
or
prefix = /usr/
or
prefix = /usr/bin/

None of the above seem to solve this.  ](*,) 
Does anyone have any suggestions?

---

