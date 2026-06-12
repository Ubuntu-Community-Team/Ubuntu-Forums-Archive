---
title: "How do I get my force fsck back"
date: 2006-08-06
forum: General Help
---

### Post by hanzomon4 on 2006-08-06
I don't what happened but I noticed after installing dapper the fs is no longer checked after being mounted 30 or more times. 
This has caused me to get some errors.
I know to force check manually but I really want the it to be automatic.

---

### Post by Ramses de Norre on 2006-08-06
What's the content of your /etc/fstab?
The last digit of the line for the partition you want to be checked must be a 1.

---

### Post by der_joachim on 2006-08-06
tune2fs -c 30 /dev/hdXY 

X is the letter of your harddrive, Y is the number of the partition. Good luck.

---

### Post by hanzomon4 on 2006-08-06
> **Ramses de Norre said:**
> What's the content of your /etc/fstab?
The last digit of the line for the partition you want to be checked must be a 1.
This is the drive in question

```
/dev/sda2       /               ext3     defaults,user_xattr,errors=remount-ro      1
```

---

### Post by hanzomon4 on 2006-08-06
> **der_joachim said:**
> tune2fs -c 30 /dev/hdXY 

X is the letter of your harddrive, Y is the number of the partition. Good luck.

I have done this before and it shot past 30... nothing happened (no force fsck), but I will try it again :wink:

---

### Post by hanzomon4 on 2006-08-09
Nope did not work, but I do know remember editing my fstab for beagle.
I think thats where the problem came from, So if anyone could post there fstab or just the root partition I think that would fix it.

---

### Post by Ramses de Norre on 2006-08-09
Mine:
```
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1

```
So just add another 1 to yours ;)

---

### Post by hanzomon4 on 2006-08-10
Like this ```
defaults,user_xattr,errors=remount-ro 0      1
```

---

