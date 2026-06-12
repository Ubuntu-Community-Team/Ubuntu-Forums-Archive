---
title: "Problem resizing my NTFS partition"
date: 2007-02-14
forum: General Help
---

### Post by nawk168 on 2007-02-14
I'm trying to shrink the size of my NTFS to make more space for my ext3 linux partition. I tried partition magic in Windows but it keeps giving me an error whenever I try to do it. I also tried the GParted Live CD which also gives me errors. In GTParted, it has fails to perform "ntfsresize -P --force --force /dev/sda1"

I was able to shrink my ext3 partition in GParted so I could make my fat32 partition (for sharing files between windows and linux) bigger with no problems.

Before I installed ubuntu, I set up the partitions with QTParted. When I try to use that now, the resize/move option is grayed out. Do you think that QTParted messed up my NTFS when I used it to set up the partitions to install linux and that's why I can't resize my NTFS anymore?

Can anyone think of any solutions to fixing this problem?

---

### Post by meng on 2007-02-14
Have you defragged your NTFS partition so that there isn't any data towards the end of the partition?

---

### Post by nawk168 on 2007-02-14
Yes I tried that the first time I got the error in partition magic. I keep getting the same error after I did it.

---

### Post by dcstar on 2007-02-14
> **nawk168 said:**
> I'm trying to shrink the size of my NTFS to make more space for my ext3 linux partition. I tried partition magic in Windows but it keeps giving me an error whenever I try to do it. I also tried the GParted Live CD which also gives me errors. In GTParted, it has fails to perform "ntfsresize -P --force --force /dev/sda1"

I was able to shrink my ext3 partition in GParted so I could make my fat32 partition (for sharing files between windows and linux) bigger with no problems.

Before I installed ubuntu, I set up the partitions with QTParted. When I try to use that now, the resize/move option is grayed out. Do you think that QTParted messed up my NTFS when I used it to set up the partitions to install linux and that's why I can't resize my NTFS anymore?

Can anyone think of any solutions to fixing this problem?

On the assumption that you have unmounted this partition before working on it, I'm not really sure what the issue is.

Is your NTFS a "Basic" or "Dynamic" disk?, if Dynamic then you could have a lot of problems resizing.

I previously used a stand alone Linux based utility CD to successfully resize a NTFS partition:

[http://www.sysresccd.org/](http://www.sysresccd.org/)

---

### Post by nawk168 on 2007-02-14
I have no idea if it's basic or dynamic. How can I find out? Which program did you use in that rescue CD to perform your partitioning? It says it has GParted but I already know that doesn't work for me.

---

