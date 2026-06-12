---
title: "wine install problems"
date: 2006-10-16
forum: General Help
---

### Post by markg729 on 2006-10-16
i was following this [http://www.ubuntuforums.org/showthread.php?t=149585&highlight=internet+explorer+wine](http://www.ubuntuforums.org/showthread.php?t=149585&highlight=internet+explorer+wine) guide to install wine and when i got to the part about installing DCOM98 it  says the installation has seemed to have failed, heres the code from when i clicked on install DCOM98

```
Choice is DCOM98 with checked=F
dcom98.exe to check
software installation verified by /home/mark/.wine/winetools.log
1229056 bytes previously downloaded
WINEDEBUG="fixme-all" WINEDLLOVERRIDES="ole32=n" wine ./dcom98.exe
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
Failed: 199
check installation by return value...
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
Failed: 199

```

can anybody help me with this?

---

### Post by ciscosurfer on 2006-10-17
Check [IEs4linux here]("http://www.tatanka.com.br/ies4linux/page/Main_Page"), or check the [WINE homepage]("http://www.winehq.com/") to explain how to install WINE from WineHQ.

---

