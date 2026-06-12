---
title: "[SOLVED] Freespace not found after resizing ext3 partition"
date: 2007-10-30
forum: General Help
---

### Post by flamacue on 2007-10-30
Hi all,

Running Ubuntu Feisty Desktop on my Dell Inspiron 700m laptop.  My root partition is /dev/sda6, which is (of course) the 2nd logical partition inside the extended partition.

I was running out of space, so decided to resize.  Booted a live CD of some sort (super grub disk, or system rescue cd), and enlarged it to the right with GParted.  When booting with either of the mentioned live cd's, and mounting the partition (which then appears as hda6, not sda6), everything looks as expected, i.e. space used, freespace (10GB free), etc.

However, when I boot into Ubuntu, it doesn't see the added space.

```
df -h
```
shows
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              20G   18G  559M  98% /
```

Whereas it should say around 30 GB total size, with 10 GB free.

How do I fix this?  Is there some cached metadata about the partition that I can clean so that it mounts it fresh?

Thanks to any who can help.


EDIT:  Is there a better place to put this question, vs. in "general support" as it is now?

---

### Post by flamacue on 2007-11-04
Solved:

Prior to resizing the partition originally (weeks ago), I made a copy of it, in case anything went wrong. I put the copy of the partition inside /dev/sda4 (it was sda7, actually). It had the same name (disklabel or what have you, "ubuntu_root" in this case) as sda6, or maybe it had one character appended, I'm not sure.

So, I don't know what the conflict was, but deleting the backup partition solved the issue. (Since I was still booting into the enlarged partition just fine, aside from the size issue, I figured it was safe to get rid of the backup.)

---

