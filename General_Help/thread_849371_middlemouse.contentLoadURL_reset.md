---
title: "middlemouse.contentLoadURL reset"
date: 2008-07-04
forum: General Help
---

### Post by JimJey on 2008-07-04
I'm running windows and ubuntu side by side on different partitions. From the firefox version running on windows I am accustomed to click the middle mouse button on a link to open a new tab. Sometimes however I don't quite hit the link: in windows it's no problem (nothing happens), in ubuntu however the clipboard contents are loaded. I want to use firefox in the same way in ubuntu as in windows.
As I wanted to share all data (bookmarks, etc.) between both platforms I created a soft link to the profile that resides on the windows partition and moved the link into the .mozilla directory. It works as expected (both versions are in sync).
However when I want to change the middlemouse.contentLoadURL behaviour (setting it to false in ubuntu) it gets reset to true after a reboot. In windows middlemouse.contentLoadURL is always false regardless of the ubuntu setting.
Where are those settings stored? Are these settings profile-independent? How can I set middlemouse.contentLoadURL to false permanently?

Thanks for your help.

---

### Post by JimJey on 2008-07-11
Does anybody have an idea?

---

### Post by linuxd00 on 2008-07-11
the "paste content of clipboard" behavior on middle click is linux dependent. So you can deactivate it in linux somewhere.

I once reconfigured by xorg.conf and got it off.(not on purpose nor desire). since then i have the behavior you want.. sorry i cant tell you what i did since i myself dont know.. i would like to get that paste functionality back tho...

so maybe fiddle something on xorg.conf?

---

