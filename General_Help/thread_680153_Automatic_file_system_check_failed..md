---
title: "Automatic file system check failed."
date: 2008-01-27
forum: General Help
---

### Post by DMBoricua on 2008-01-27
Hello, before I could post this error I have done some research on how to fix this myself, but just to make sure, I'm posting it to see what response I get.

I could put the Live CD to check the problem like people would say, but I have the 7.04 version on the disc, not 7.10.

I've got a photo that I've taken regarding to the problem: 

[http://img502.imageshack.us/img502/559/cimg1224vs6.jpg](http://img502.imageshack.us/img502/559/cimg1224vs6.jpg)

The picture is pretty self-explanatory, what should I do? :confused:

---

### Post by lizadove on 2008-01-27
Hi, I had the exact same error, and I ended up installing ubuntu again in a different partition - guess what - when I started it up, it fixed the errors in the first partition!  Cool, huh?  So, I wasn't able to "directly" fix the problem, but I thought I'd share what worked for me.

---

### Post by taurus on 2008-01-27
At the prompt, run

```
fsck -y /dev/hdc1
```

---

### Post by DMBoricua on 2008-01-27
Thanks! :) That worked great. Typing this reply on Ubuntu completely fixed!

I'm curious to know what has caused this problem, though, is there an explanation?

---

### Post by taurus on 2008-01-27
How have you shut down your machine?  Pushing the power button to shut it down is not a great idea.  It leads to problems with the filesystem and you have to run fsck manually to fix them.

---

### Post by DMBoricua on 2008-01-27
I dont recall doing a hard boot on Ubuntu ever before I've gotten this problem, but if you're talking about after the fixing on the prompt, I just hit Control+D and it did a restart.

---

### Post by articpenguin on 2008-01-28
if your using ext2 and you hard poweroff or hard reset you will have to run fsck. IF you use a journalling filesystem like ext3 then chances are you wont run fsck because all changes are logged in the journal.

---

