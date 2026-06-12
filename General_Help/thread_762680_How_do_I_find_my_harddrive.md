---
title: "How do I find my harddrive"
date: 2008-04-22
forum: General Help
---

### Post by joeri_83 on 2008-04-22
Hi

I used to have XP on sda and Ubuntu on sdb (dual boot), but I threw XP out and reformatted sda to ext 3. My question is simply: what is the location of this in my file system?

---

### Post by schmildo on 2008-04-22
Before I start i'm not running ubuntu at the moment and i'd normallly test these commands before posting so they might not be exact, but they should get you going.

I reckon you're probably booting from sdb at the moment right?
So if you've formatted sda to ext3 you'll have:


/dev/sda ext3
/dev/sdb <possibly ext3>

if you type: fdisk -l

you should see both sda and sdb, only trouble is if you type: df -ah
you won't see sda anywhere, but that's no troulble, all you gotta do is mount it somewhere so...

make a folder somewhere, say /home/user/myoldxppartition and in the terminal type:
mount /dev/sda /home/user/myoldxppartition

then you should be able to add files to that folder in the knowledge that it's filling up all the space on sda, which I think you can confirm by typing: df -ah

rock on brother

(oh and simply typing "mount" will show you what you have mounted and where)

---

### Post by joeri_83 on 2008-04-22
Thanks.

When I try to mount it I get this message:
```
mount: you must specify the filesystem type
```

Have I missed something? GParted tells me the disk is ext3.

---

### Post by markjensen on 2008-04-22
What did you try to "mount" that failed?  The command you used would be helpful.

Also, let's make sure you are specifying the right partition in your command by listing out what you have.  That is the **sudo fdisk -l** (that's a lowercase letter "L", not the number one) command mentioned earlier.

---

### Post by joeri_83 on 2008-04-22
Oops, missed a one when I typed in sda1. Clumsy of me. Thanks to the both of you for taking the time to help me!

---

### Post by markjensen on 2008-04-22
Cool.  Glad you got it solved!

---

