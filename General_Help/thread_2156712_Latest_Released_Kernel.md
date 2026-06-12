---
title: "Latest Released Kernel?"
date: 2013-06-22
forum: General Help
---

### Post by JSeymour on 2013-06-22
Hi All,

How can I easily find out what is the current latest stable kernel version for a particular release?  (IOW: What I'd be running if I was up-to-date?)

Thanks,
Jim

---

### Post by howefield on 2013-06-22
"apt-cache search term" if you have an up to date package list ?

eg

```
apt-cache search linux-image | grep kernel
```

Or you could look at the kernel section on packages.ubuntu.com or you could subscribe to the relevant mailing list.

---

### Post by grahammechanical on 2013-06-22
It depends what you call "stable." The Linux developers have a different understanding of "stable" to the Ubuntu developers. The very latest Linux kernel would not be used straight away in Ubuntu. Unless you took special steps to install it you would need to upgrade to a newer version of Ubuntu to get more up to date kernels. If you was running Saucy Salamander right now you would be using kernel 3.9.0-6. Saucy may get the 3.10.0 series by the time it is released. Raring Ringtail was at 3.8.0-25 or there abouts.

Regards.

---

### Post by JSeymour on 2013-06-23
Got it, guys.  Thanks!

Jim

---

