---
title: "problem: no access seagate external hdd"
date: 2007-11-05
forum: General Help
---

### Post by si4u on 2007-11-05
hi,

please forgive if my english is not correct ( i'm from holland)

friday I've installed ubuntu 7.10 in just one word AWESOME!

but I got one problem.
I got a Seagate External hdd and ubuntu doesn't show it on the desktop.
I can't see it in 'My Computer' too.
but when I look at my hardware info its there...
so where can I get access to my EHDD??

anyone an idea :confused:
please help!

thnx

---

### Post by callan79 on 2007-11-05
> **si4u said:**
> 
friday I've installed ubuntu 7.10 in just one word AWESOME!
I got a Seagate External hdd and ubuntu doesn't show it on the desktop.
I can't see it in 'My Computer' too. but when I look at my hardware info its there...
so where can I get access to my EHDD??

Hello,

Is the hard drive USB ?

Can you plug your hard drive in do this :

```

sudo fdisk -l

```

Please paste your results here so we can see.

Thanks
Callan

---

### Post by si4u on 2007-11-05
yes it is an USB HDD

okay I'll try
but I can do it in the afternoon because I'm at my work right now.

but I'll tell you

thnx

---

### Post by si4u on 2007-11-05
this is what I get:

/dev/sdc is the EHDD

[IMG]http://img132.imageshack.us/img132/8913/konsoledg5.png[/IMG]

---

### Post by callan79 on 2007-11-06
> **si4u said:**
> /dev/sdc is the EHDD

Hello,

Looks like your system can see the partition anyway, that's a good thing!

What about this :

```
mount
```

Also, if you go to Places >> Computer, can you see the drive listed there?

Cheers
Callan

---

### Post by si4u on 2007-11-06
yes ubuntu see it. it knows the type and number.

no it isn't in the computer list

i'll try mount

---

