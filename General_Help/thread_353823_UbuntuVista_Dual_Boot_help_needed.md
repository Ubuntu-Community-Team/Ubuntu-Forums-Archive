---
title: "Ubuntu/Vista Dual Boot help needed"
date: 2007-02-05
forum: General Help
---

### Post by djevoultion on 2007-02-05
hey im new here

i recently installed ubuntu/linux dual boot setup on my computer but i have a small problem. i have googled it (believe me) but i cant find the solution to "how can i access my ubuntu partition in vista and how can i access my vista partition in ubuntu" if anyone knows how i can do this please help...

---

### Post by mrfuzzemz on 2007-02-05
I haven't used Vista since the release candidates, but does it use an NTFS filesystem?

If so then you can use ntfs-3g.  It is a newer ntfs driver for linux that allows read-write support.  Check out this thread on how to set it up:

[http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g)

If you have trouble just let me know as I mount my XP disk with it and it works great.

Also note at the top of the post in red  it has a link to fs-driver.  You can use this to access ext2 (and ext3 too, I think) in windows.
Let me know if you get it going!

---

### Post by dustman on 2007-02-05
I have a similar problem....the difference is that I cand see my vista partition, but I can't make the system boot on vista (the grub loader shows me that I can boot only on Ubuntu) ... any suggestions are welcomed :D

---

### Post by djevoultion on 2007-02-06
thanks for your reply but apparantly vista uses a different kind of ntfs file sytem than xp.. or its preventing access to it via other operating systems.. ive just decided to create  a seperate partition which both os's can access.

---

