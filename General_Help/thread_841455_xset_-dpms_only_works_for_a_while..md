---
title: "xset -dpms only works for a while."
date: 2008-06-26
forum: General Help
---

### Post by chrismyers on 2008-06-26
Hi Guys,
 
I want to permanently disable dpms to prevent screen blanking.
 
I do an:
 
xset -dpms
 
Then an:
 
xset -q
 
to confirm that dpms is off. Everything is OK for a while until DPMS flips back on!
 
Can anyone help with keeping it off or removing it completely?
 
Cheers.

---

### Post by mali2297 on 2008-06-26
Add these lines to the end of the file /etc/X11/xorg.conf:
```

Section "ServerFlags"
        Option          "blank time" "0"
        Option          "standby time" "0"
        Option          "suspend time" "0"
        Option          "off time" "0"
EndSection

```

---

