---
title: "How do I mount .iso files?"
date: 2008-05-12
forum: General Help
---

### Post by grs on 2008-05-12
Is there an optical drive emulator in Ubuntu, I have an ISO file I want to load.

---

### Post by Monicker on 2008-05-12
You can install gmountiso or kiso for that.  They are both in Synaptic.

---

### Post by noerrorsfound on 2008-05-12
You can use the mount command:
```
sudo mount -o loop YourFile.iso /home/user/where-you-want-to-mount-files
```

---

