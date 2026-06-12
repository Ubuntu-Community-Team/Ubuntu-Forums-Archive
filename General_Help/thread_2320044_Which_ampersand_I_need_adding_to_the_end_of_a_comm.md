---
title: "Which ampersand I need adding to the end of a command"
date: 2016-04-09
forum: General Help
---

### Post by satimis on 2016-04-09
Hi all,

Which ampersand I need adding to the end of a command not locking the terminal?

Example:
&#10219; VBoxHeadless -s "pfsense" &```

[1] 10128
satimis@ub1404ssd1tb:~&#10219; Oracle VM VirtualBox Headless Interface 5.0.16
(C) 2008-2016 Oracle Corporation
All rights reserved.


```
pfsense started but the terminal being locked.  "&" didn't work

Thanks

satimis

---

### Post by montag dp on 2016-04-09
Are you sure it locked? A lot of times applications will continue to write output to terminal, even if you started it with & at the end if the command, but you can still use the terminal to issue new commands. (Although, it is pretty annoying to try to use a terminal like that. I usually just hit Ctrl+Shift+n to launch a new one in the same directory in that case.)

---

### Post by satimis on 2016-04-09
> **montag dp said:**
> Are you sure it locked? A lot of times applications will continue to write output to terminal, even if you started it with & at the end if the command, but you can still use the terminal to issue new commands. (Although, it is pretty annoying to try to use a terminal like that. I usually just hit Ctrl+Shift+n to launch a new one in the same directory in that case.)
Hi,

Sorry, I forgot hitting "Enter" for continue using the terminal to issue new commands

Thanks

Regards
satimis

---

