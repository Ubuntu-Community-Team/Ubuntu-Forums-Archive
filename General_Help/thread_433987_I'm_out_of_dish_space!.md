---
title: "I'm out of dish space!"
date: 2007-05-05
forum: General Help
---

### Post by rab4567 on 2007-05-05
Help Help Help! Ok guys I feel real dumb right now but, I have completlely run out space on my partition so much so I can't even log in. On the bright side I did purchase a new seagate 500gb internal hard drive so I knew it coming down the road but not quit this soon so I'll need help with that too.

---

### Post by jfinkels on 2007-05-05
> **rab4567 said:**
> Help Help Help! Ok guys I feel real dumb right now but, I have completlely run out space on my partition so much so I can't even log in. On the bright side I did purchase a new seagate 500gb internal hard drive so I knew it coming down the road but not quit this soon so I'll need help with that too.

If you want to move files from one partition to another, boot into the Live CD environment, then mount both the partitions (the source one and the target one) and move files to your heart's content.

---

### Post by bapoumba on 2007-05-05
Boot in recovery mode, you'll be root (with a # prompt):
```
# df -H
```
will tell you which partition is full.
```
# aptitude clean
```
will make some room on your root (/) partition
Look in your /home for files to remove
```
reboot
```

---

### Post by ticopelp on 2007-05-05
Out of dish space? Well, you'll either have to remodel your cupboards or not have so many beer steins up there, I guess.

---

### Post by rab4567 on 2007-05-05
My immediate problem is I can't even log in, it says not enough memory see administrator. If I could get in I would create more space on my partition but I'm stuck now ,

---

### Post by rab4567 on 2007-05-05
thanks guys

---

### Post by meng on 2007-05-05
Did you boot in recovery mode as suggested by bapoumba?

---

