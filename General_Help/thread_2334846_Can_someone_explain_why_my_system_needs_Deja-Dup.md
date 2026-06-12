---
title: "Can someone explain why my system needs Deja-Dup?"
date: 2016-08-23
forum: General Help
---

### Post by zuto2 on 2016-08-23
Today I found out that Deja-Dup was a back up tool that apparently does not even work on my computer. I click it and it does not launch, but apparently it fixed my system settings from crashing.

My issue was here:
[https://ubuntuforums.org/showthread.php?t=2334797](https://ubuntuforums.org/showthread.php?t=2334797)


Deja-Dup installed quite a few packages? Are the other packages store in Deja-Dup?
[IMG]https://s15.postimg.io/nxu8sibjf/Selection_003.png[/IMG]

---

### Post by grahammechanical on 2016-08-23
I am going to guess. You removed deja-dup? That action removed several other packages that were dependencies of deja-dup or rather deja-dup was dependent on them and so you then had system errors. Re-install deja-dup and the system errors go away.

Did you use the purge command?

---

### Post by zuto2 on 2016-08-23
I never removed deja-dup. I think an update might have done it or maybe an autoremove. I never knew that it existed until yesterday.

---

### Post by oldrocker99 on 2016-08-23
I use grsync, which does a bang-up job of backing up (and once, restored) my /home folder. There are several backup programs available, and, while I prefer grsync, your mileage might vary.

---

### Post by zuto2 on 2016-08-24
I guess all that matters is that deja-dup fixes my System settings. I actually TAR my whole system as root with the terminal and restore it. My process requires me to edit the old swap out and grub restore, but it does not take long at all. I will have to test my system out before backing up again. I might miss minor errors again like deja-dup....

I know the restore did not break the system settings because I have done this quite a few times.

---

