---
title: "Is there a command to fix errors or something??"
date: 2008-06-13
forum: General Help
---

### Post by morbid_bean on 2008-06-13
Im sure this sounds dumb but Is there a such thing as a thing where u can scan your unbuntu intall for errors? and fix them?

Using ubuntu 8.04

---

### Post by cariboo on 2008-06-13
In a terminal type:

```
man fsck
```

That will give you everything you want to know about **fsck**.

Jim

---

### Post by bingoUV on 2008-06-13
what kind of errors do you suspect? What are the symptoms? What wrong did happen to the computer that you suspect errors?

---

### Post by morbid_bean on 2008-06-13
> **bingoUV said:**
> what kind of errors do you suspect? What are the symptoms? What wrong did happen to the computer that you suspect errors?



I suspect some problems with my sound in certian areas....diffrent things happen each time...lol hard to explain.

---

### Post by VMC on 2008-06-13
> **morbid_bean said:**
> I suspect some problems with my sound in certian areas....diffrent things happen each time...lol hard to explain.

Have you checked System-Preferences-Sound and check there for any problems?

Also check System-Administration-System Log files for any issues about sound.

---

### Post by ramjet_1953 on 2008-06-13
After about 30 mounts, your system automatically checks for disk errors with fsck.

**_DO NOT_** use fsck on a mounted drive, as it can do horrible things.

What I mean by this is **_DO NOT_** type [COLOR="Red"]fsck<drive>[/COLOR] in a terminal where <drive> is the HDD you are currently operating from.

If you only have the one drive and you have a need to check it, use your Ubuntu install disk to check your hard drive , using the fsck command.

Regards,
Roger :cool:

---

