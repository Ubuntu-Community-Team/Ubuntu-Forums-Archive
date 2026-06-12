---
title: "Partitioning"
date: 2014-02-12
forum: General Help
---

### Post by jainabk on 2014-02-12
Hey I am using the attached configuration in my storage:

[ATTACH=CONFIG]250284[/ATTACH]

I want to take 10 gb out of sda6(/home) and put in sda1(/).

Is it possible? How to go about it?

---

### Post by NM5TF on 2014-02-12
> **jainabk said:**
> Hey I am using the attached configuration in my storage:

[ATTACH=CONFIG]250284[/ATTACH]

I want to take 10 gb out of sda6(/home) and put in sda1(/).

Is it possible? How to go about it?

yes it is possible......go here for the guide to partitioning:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

tommy

---

### Post by Impavidus on 2014-02-12
Shrink sda6 from the left, turn swap off, shrink sda2 from the left, expand sda1 to the right, all from the live disk (which you already run).

This is a slow and somewhat dangerous action, as sda6 is almost full too. Data will have to be moved around on an already nearly full partition, which takes time. If anything goes wrong (power failure, for example), you may lose your data. Make sure you have backups of all important files. With sda6 almost full, performance may be worse.

I always wonder how people fill their hard drives. After 2½ years on this laptop, I filled just 20GB of the 320GB drive.

---

### Post by jainabk on 2014-02-14
Thanks a lot Impavidus. That really helped.

---

