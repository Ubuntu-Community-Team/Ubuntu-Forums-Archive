---
title: "Can't see NTFS partition..."
date: 2007-12-17
forum: General Help
---

### Post by JustBrowsing on 2007-12-17
This might already addressed, but I'm not entirely sure.

First, let me say I love the entire concept of Wubi and everything about it, sure it's not the optimal experience for using Linux and Ubuntu - but it works great! A big thank you to all that is involved. I love being able to install this and things "just working."

However, I just installed Ubuntu 7.10 with Wubi 7.10 (Alpha release), while the install was pretty seamless without any error, I cannot access my files on my Windows XP partition which is formatted NTFS.

There is a error message when I boot into "Ubuntu-linux" saying something about the partition type being NTFS and I think b0 or something. It only lasts on screen for maybe 2 to 3 seconds.

I've heard people saying they're receiving a "Error 13" type of error, but this is nothing of the sort, I can't even write down what it's saying then "Press any key to continue..." it just boots into Ubuntu.

My partitions are kinda screwy because of this stupid Dell PC and me trying to keep the recovery partition/ Media Manager/ and another "Diagnostic" partition all intact. If it wasn't for that - I'd just install Ubuntu 7.10 natively, and go that route.

Again, thanks to all for any help  you can give me, and for this great alternative to a true native installation.:)

The Wubi version I used was:
Wubi-7.10-alpha-rev386

---

### Post by ago on 2007-12-18
The drive where you installed wubi should be available as /host
The other drives should be available under /media

---

### Post by JustBrowsing on 2007-12-18
> **ago said:**
> The drive where you installed wubi should be available as /host
The other drives should be available under /media

That did it! Thanks so much, I saw something posted like this before, but I never checked it. Excellent... thanks so much. :):popcorn:

---

### Post by allforcarrie on 2008-01-03
wow! i have been using WUBI for 2 months and didnt notice that! awesome!!!

---

