---
title: "Source of RT Kernel"
date: 2008-06-04
forum: General Help
---

### Post by Tehut on 2008-06-04
Hi,

could someone please tell me where I can get the source of the current ubuntu rt kernel? Need it to get virtualbox running.

Thank you.

---

### Post by Tehut on 2008-06-04
bump

---

### Post by TransitMan on 2008-06-04
Why do you need the RT kernel to get VirtualBox running?
Are you running a specialized setup or something?

I use VB with the lastest kernel image from the repos, and it works just fine.

---

### Post by RAOF on 2008-06-05
```
sudo aptitude install linux-headers-rt
```

---

### Post by Tehut on 2008-06-05
RAOF: Thank you. No wonder I didn't find anything, totally forgotten to install that.

---

