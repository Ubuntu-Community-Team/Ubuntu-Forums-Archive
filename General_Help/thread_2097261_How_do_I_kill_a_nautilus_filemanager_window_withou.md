---
title: "How do I kill a nautilus filemanager window without resetting the desktop?"
date: 2012-12-22
forum: General Help
---

### Post by Wim Sturkenboom on 2012-12-22
Ubuntu 12.04

There is this highly annoying bug in Nautilus where Nautilus simply hangs when calling up the properties of certain file types (raw image files from digital cameras).

I can kill nautilus in a terminal or force quit it, but next my conky display is gone. So how do I kill / force quit nautilus without resetting the desktop?

---

### Post by mcduck on 2012-12-22
Not possible. The desktop is handled by Nautilus, so killing Nautilus will restart the desktop as well.

Try restarting Conky afterwards instead.

(or take a look if there might be a way to fix the issues with viewing raw files properties... Perhaps there's a Nautilus extension that would help, or maybe you have already installed one that isn't compatible with current Nautilus version and need to uninstall it... Have you checked the ~.xsession-errors if there's any relevant error messages?)

---

### Post by ibjsb4 on 2012-12-22
Have you tried

```
killall nautilus
```

---

