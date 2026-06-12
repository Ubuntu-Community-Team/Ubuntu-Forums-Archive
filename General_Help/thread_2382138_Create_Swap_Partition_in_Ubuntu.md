---
title: "Create Swap Partition in Ubuntu"
date: 2018-01-09
forum: General Help
---

### Post by prakashpnvps on 2018-01-09
I am trying to create a swap partition in Ubuntu. I have moved from windows to Ubuntu. While trying to shrink sda2 through GParted, it is not allowing to create more than 4 partitions. Can I delete sda1 or sda3? What is the purpose of them?
Is there any way to create swap partition without deleting them.
[ATTACH=CONFIG]278105[/ATTACH]

---

### Post by deadflowr on 2018-01-09
Do you still want to use Windows?

---

### Post by howefield on 2018-01-09
What version of Ubuntu are you using ?

```
cat /etc/*-release
```

If later than 17.04 it will have a swap file instead of a swap partition.

---

### Post by prakashpnvps on 2018-01-09
yes, for future use.

---

### Post by prakashpnvps on 2018-01-09
I am using 16.04. I think swap partition is allowed for this version.

---

### Post by Yellow Pasque on 2018-01-09
You can't have more than 4 primary partitions. You would need to delete at least one partition and create an extended partition. It would be easier to create a swap file.

---

### Post by prakashpnvps on 2018-01-09
What are sda1 and sda3 with flags boot and diag for?

---

### Post by deadflowr on 2018-01-09
well you can't boot into Windows with sda1, so you need that.
sda3 should be a recovery partition, which is not really necessary but nice to have if things go night night ( I guess?).
Personally I would blow out Ubuntu and make that partition the extended partition and then you can create as many partitions as you want inside that.
I mean you shouldn't have that much in terms of personal data on it and reinstalling everything won't take too long.

---

