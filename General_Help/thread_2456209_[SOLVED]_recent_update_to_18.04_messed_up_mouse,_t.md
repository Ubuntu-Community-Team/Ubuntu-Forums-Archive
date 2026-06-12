---
title: "[SOLVED] recent update to 18.04 messed up mouse, text selection, etc"
date: 2021-01-06
forum: General Help
---

### Post by riverhawk on 2021-01-06
Hello everyone, 

Over the past week or so one of the updates I installed to my system messed up the functioning of my mouse. For example how it double clicks, selects text, moves around windows, etc. I was wondering if a good fix would be to rollback the kernel and than block that update. And, if so, which kernel would be advised to rollback to and how would I go about doing this.

Thanks for any help or pointers to get more information!

---

### Post by Impavidus on 2021-01-07
This sounds more like a problem with the window manager than with the kernel.

Old kernels aren't removed automatically (at least, not at once). You can use the grub menu to boot an older kernel and see if the problems happens there too. To see a list of recently upgraded packages, use```
grep " upgrade " /var/log/dpkg.log
```

---

### Post by ActionParsnip on 2021-01-07
If you boot an older kernel, is it OK?

---

### Post by riverhawk on 2021-01-07
Hi Impavidus and ActionParsnip, thanks for the replies.

First off, now things are better, so I'll mark it solved. Not sure if another update just fixed things or some dumb problem on my end.

Thanks for the information on booting the older kernel and also how to grep through dpkg.log. Booting the older kernel didn't change anything. And I did start going through the windows manager settings, so maybe that's what fixed it.

Again, thanks...I was in panic about this for two days, so I'm glad things are working again!

---

