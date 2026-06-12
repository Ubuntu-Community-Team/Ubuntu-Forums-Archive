---
title: "Wine Apps at Session Startup / General Startup help"
date: 2007-09-16
forum: General Help
---

### Post by TB2 on 2007-09-16
Hi,

I need two wine emulated progs to automatically start when gnome is starting up. E.g. I tried adding ```
wine /home/_myusername_/.wine/drive_c/Program Files/Proxomitron/Proxomitron.exe
```to the sessions manager, or also just the path without "wine" in front of it but neighter are working. I also tried starting them up and then hit "save current seission", which didn't work eighter. I couldn't find any information on this searching the forums and the net.

The secons question is: How can I tell a program to autostart on viewport/desktop/workspace no. 2 instead of 1. I want to start the Proxomitron hidden (I guess --start-hidden should do the job) and I want Trillian and rythmbox to be loaded on viewport 2. I also want them to start at a certain X/Y position and a particular size. How can I do that?

Your help would be appreciated,
TB2

---

### Post by happy-and-lost on 2007-09-16
You need to put it into a bash script. In a terminal...

*nano .Proxomitronstart*

Paste into there...

```
#!/bin/bash
wine /home/_myusername_/.wine/drive_c/Program Files/Proxomitron/Proxomitron.exe &
exit
```

Press Ctrl+O to save, Ctrl+X to exit, then

*chmod +x .Proxomitronstart*

Then add your .Proxomitronstart file to the session startup thing.

For your second question, do a search for devilspie. It does what you want.

---

