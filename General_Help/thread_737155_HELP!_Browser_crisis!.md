---
title: "HELP! Browser crisis!"
date: 2008-03-27
forum: General Help
---

### Post by GTengineer on 2008-03-27
Hi everyone, I am having problems with both my browsers (Firefox and Opera). Both of them are crashing whenever I try to start them.

I have tried autoremoving firefox and reinstalled it with sudo apt-get install firefox but still get the same proble when I launch Firefox it produces this error:
[ATTACH]64025[/ATTACH] <--- click to expand
When I look under system monitor I do not see any opened firefox services.

When I open Opera it opens briefly and quickly closes and gives this error
```
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Segmentation fault (core dumped)

```

Can anyone help? I am a Linux noob and I don't even know where to start fixing this problem. Thanks!

---

### Post by cdenley on 2008-03-27
If after restarting your computer, firefox still gives you the same message, this should fix it but delete any browser data like bookmarks or cookies.
```

rm -rf ~/.mozilla

```

---

### Post by GTengineer on 2008-03-27
> **cdenley said:**
> If after restarting your computer, firefox still gives you the same message, this should fix it but delete any browser data like bookmarks or cookies.
```

rm -rf ~/.mozilla

```

Thank you, that fixed firefox!

I did the same "rm -rf .opera" but did not fix the problem with Opera.

---

