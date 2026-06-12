---
title: "Beryl won't start"
date: 2006-10-14
forum: General Help
---

### Post by Crashmaxx on 2006-10-14
I installed beryl and have it working (well, at least it didn't crash) but I can't get any effects. I tried just running beryl in terminal and got this error:
```
crash@crashbox:~$ beryl
XGL Present
beryl: No XKB extension
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

```

And everything is running very slow. But beryl-manager is working fine in my taskbar. Any ideas?

---

### Post by pay on 2006-10-14
Are you driver setup correctly? Are you using AIGLX with FGLRX driver? because with the FGLRX driver AIGLRX doesn't work, yet.

---

### Post by Crashmaxx on 2006-10-14
Just delete this, I am using partimage to restore it to normal as we speak.

I had XGL and beryl on an old nvidia card. I thought I had it configured right, but I guess not. Its a slow machine, so I think I'll just wait till beryl is at least a beta, and I have done some upgrades to my machine.

Thanks though.

---

