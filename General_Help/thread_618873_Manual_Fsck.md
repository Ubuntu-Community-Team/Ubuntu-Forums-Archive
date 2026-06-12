---
title: "Manual Fsck"
date: 2007-11-20
forum: General Help
---

### Post by aliciapg on 2007-11-20
Help? I don't know how to do a manual fsck.

---

### Post by por100pre1 on 2007-11-20
You can do this:

```
sudo touch /forcefsck && sudo reboot
```

---

### Post by aliciapg on 2007-11-21
I tried a bunch of other stuff and it randomly worked.... I don't even know how.... So I never got to try that...
But thanks for the help though. I will have to remember that because I'm sure it will happen again.... But thanks!!

---

### Post by por100pre1 on 2007-11-21
Another way is to boot from the LiveCD and manually scan the **unmounted** device like this for e.g. hda1:

```
sudo fsck -f /dev/hda1
```

**Doing that to a mounted device can ruin your data if repairs are performed.** So you better use the previously posted method, it is less risky.

---

### Post by aliciapg on 2007-11-23
Alright, because, yeah, I don't want to delete everything that would be bad.... Thanks for your help!

---

