---
title: "How to check if LLVMpipe or full accelerated Unity 3D graphics is in action?"
date: 2012-10-21
forum: General Help
---

### Post by abcuser on 2012-10-21
Hi,
I installed Ubuntu 12.10 on my notebook. During install there was no question if I would like to have full accelerated Unity 3D or using low graphics LLVMpipe, Ubuntu install does this by itself. How can I check which one is actually applied in my case?
Thanks

---

### Post by mc4man on 2012-10-21
You could see what this shows - 
```
sudo apt-get install mesa-utils
```
```
glxinfo |egrep 'OpenGL|vendor|rendering'
```

---

