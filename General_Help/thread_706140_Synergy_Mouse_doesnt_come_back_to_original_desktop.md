---
title: "Synergy Mouse doesnt come back to original desktop"
date: 2008-02-24
forum: General Help
---

### Post by Jfrench on 2008-02-24
Its a simple problem, but I can't stop it from happening. I have a gameing PC running Vista and I have a laptop that has 7.10 installed. 

The Vista pc is the Server, the laptop is the client.

Once Synergy is activated, everything seems fine. If I move  my mouse onto the laptop the pointer moves onto the laptop's screen. BUT it doesn't come back once i move it back to the same edge of the screen.


Has this happened to anyone before? Any advice would be greatly appreciated.

---

### Post by SorryGoFish on 2008-03-27
Please post your synergy config. Be sure to have both sections as:

```
section: screens
        linux:
        windows:
end

section: links
        linux:
                left = widows
        windows:
                right = linux
end
```

---

