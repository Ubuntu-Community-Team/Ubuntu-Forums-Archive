---
title: "Modify partition while hibernating"
date: 2006-11-28
forum: General Help
---

### Post by pgilmon on 2006-11-28
Hi all.

I have a laptop with windows and ubuntu and I'm planning to add support for ext2 to windows xp by using this [driver]("http://www.fs-driver.org/"). But I don't want to risk all my data, so here is my question:

What happens if I put ubuntu into hibernate, boot XP, modify the ext3 partition in which ubuntu is installed and then try to boot ubuntu again? I have read that similar actions can lead to problems [problems]("http://www.suspend2.net/FAQ.html#toc5.5") using swsusp2, but this is not the hibernate tool that ubuntu uses, so I don't know if what it says there is appliable in this case.

Note: the driver allows [mounting ext3 partitions as ext2 partitions]("http://www.fs-driver.org/faq.html#acc_ext3").

Thanks in advance.

---

### Post by taurus on 2006-11-28
If you want to resize your harddrive, try to use gparted from the LiveCD or GParted LiveCD...

---

### Post by pgilmon on 2006-11-29
Well, perhaps I didn't manage to explain what I meant. I don't need to resize my partitions. I just want to know if there is any risk in modifying the linux partition contents from Windows while linux is hibernating.

---

