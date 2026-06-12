---
title: "HELP! can't boot into any partitions!"
date: 2008-01-12
forum: General Help
---

### Post by taehC on 2008-01-12
I just took out a partition and enlarged the partition before it into the space that was the partition i deleted and now when i reboot it goes to a grub command line.  What Do I Do!?!?!?!?!??!!

---

### Post by kellemes on 2008-01-12
This isn't enough information for people to be able to help..
Please tell us about you partition-scheme, and how did you mount them, and tell us what partition you deleted etc..

---

### Post by 4real*leb on 2008-01-12
Which partition did you delete?

---

### Post by taehC on 2008-01-12
well i had my partitions set up with windows as the first partition taking up 200gb
then i had my main linux partition.
next i had a linux partition i was doing a test on(the one i just deleted)
and then at the end i had my swap

---

### Post by 4real*leb on 2008-01-12
Ok are you aware of the importance to Linux the third partition (the one you deleted) had?

---

### Post by taehC on 2008-01-12
i not exactly sure what you mean.  but my main linux partition is labeled as sda3 even though it is the second partition, if that helps...

---

### Post by 4real*leb on 2008-01-12
Can you boot into Windows? Also what version of Windows is installed?

---

### Post by taehC on 2008-01-12
well when i boot it usually goes to the partition selector but instead it just goes to a grub command line
in the command line i typed boot and it said i needed to load the kernel but when i typed kernel it says
error 22: no such partition

---

### Post by 4real*leb on 2008-01-12
Ok get SuperGrub and try using that, if you can succesfully boot into Linux (using SuperGrub) we can fix whatever went wrong with Grub.

[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

---

### Post by taehC on 2008-01-12
oh ok. i already have a supergrub cd so ill just use that

---

### Post by taehC on 2008-01-12
Thank you so much 4real*leb i think it is working now.  if i get anymore problems i post again but i think it is working! thanks!

---

### Post by 4real*leb on 2008-01-12
No Problem. Enjoy.

---

