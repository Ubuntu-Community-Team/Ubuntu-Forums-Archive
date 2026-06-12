---
title: "Wrecked install, now how do I rescue files?"
date: 2007-08-03
forum: General Help
---

### Post by MarkTBSc on 2007-08-03
I've managed to kill Ubuntu beyond my ability to even diagnose what's wrong and I don't want to pester people here to help me fix it so I've decided on a clean install.
I'd like, however to salvage my files. I can get to them with a liveCD but because the LiveCD isn't the original owner. Ubuntu won't let me touch them/copy them/play them or anything. How do I alter the permissions to let me copy everything off safely onto a USB disk?

Thanks

---

### Post by dougfractal on 2007-08-03
> **MarkTBSc said:**
> I've managed to kill Ubuntu beyond my ability to even diagnose what's wrong and I don't want to pester people here to help me fix it so I've decided on a clean install.
I'd like, however to salvage my files. I can get to them with a liveCD but because the LiveCD isn't the original owner. Ubuntu won't let me touch them/copy them/play them or anything. How do I alter the permissions to let me copy everything off safely onto a USB disk?

Thanks


use the file manager as root
```
sudo nautilus  
``` 

when finished and wish to make the files owned by you again
```
sudo chown -R user:user /pathtofolder
```

---

### Post by MarkTBSc on 2007-08-03
> **dougfractal said:**
> use the file manager as root
```
sudo nautilus  
``` 

when finished and wish to make the files owned by you again
```
sudo chown -R user:user /pathtofolder
```

Aha! Much obliged to you. I'd thought of this option but then I couldn't find where the disk was stored within the file system. I'm still not much more than a tyro when it comes to Linux but I'm learning.

Mark

---

### Post by dougfractal on 2007-08-03
> I couldn't find where the disk was stored within the file system

/media/sdXX

---

### Post by splintercellguy on 2007-08-03
sudo fdisk -l helps too.

---

