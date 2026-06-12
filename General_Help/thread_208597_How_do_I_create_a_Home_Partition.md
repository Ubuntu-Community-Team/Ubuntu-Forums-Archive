---
title: "How do I create a Home Partition?"
date: 2006-07-03
forum: General Help
---

### Post by handy on 2006-07-03
I have searched the forums, I know the info' is there but I could not find it!

What do I have to edit, & exactly how do I edit it, to move my **/home/** to its own partition?

This is probably a valuable question for many of us, as we proceed down the track with linux.

Thankyou in advance.

---

### Post by gdselzer on 2006-07-03
Make sure you have copied all your home folders to your target partition.  Then add the following to /etc/fstab:

/dev/targetpartition /home ext3 defaults 1 1

Then:
```
mount -a
```

Should be done.

---

### Post by tonyr on 2006-07-03
[This]("http://www.psychocats.net/ubuntu/separatehome.html") is what you were looking for.

---

### Post by handy on 2006-07-04
[QUOTE=tonyr][This]("http://www.psychocats.net/ubuntu/separatehome.html") is what you were looking for.[/QUOTE]

Thanks for both replies, the one I quoted is certainly the comprehensive one for a beginner like me! :KS

---

### Post by zitch on 2006-07-04
Wow, I was looking for something exactly like that, since I am replacing my laptop's 40 gig drive with a 160 gig drive, and I wanted to move /home to its own partition!  

Thanks!

---

