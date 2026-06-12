---
title: "How do I install &quot;generic kernel&quot; to get dual core support"
date: 2006-10-29
forum: General Help
---

### Post by muzzamo on 2006-10-29
Hi,

I have an athlon AM2. What is the best way to get dual core working, at the moment I am using the 2.6.17-10-386 kernel (thats what it says in Grub).

Do I need to change to the Athlon 64 kernel, or can i use this generic one?

How do I actually go about installing it so that it is there in my list of options in Grub.

Thanks

---

### Post by ~LoKe on 2006-10-29
```
sudo apt-get install linux-image-2.6.17-10-generic
```

---

### Post by muzzamo on 2006-10-29
thanks!

---

### Post by ~LoKe on 2006-10-29
> **muzzamo said:**
> thanks!

Not a problem.

---

### Post by hotani on 2006-10-29
For [some of us](http://www.ubuntuforums.org/showthread.php?t=285272) the generic kernel would not boot. If that is the case, run the fix in [this thread](http://ubuntuforums.org/showthread.php?t=282956) which should take care of it.

---

