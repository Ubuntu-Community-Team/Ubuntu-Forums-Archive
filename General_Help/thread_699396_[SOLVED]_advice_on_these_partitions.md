---
title: "[SOLVED] advice on these partitions"
date: 2008-02-17
forum: General Help
---

### Post by seventhc on 2008-02-17
OK I recently installed Ubuntu using the manual partition set up.
It's more experimental to see or find the best partitioning scheme. I know I don't need my swap so large,so no comments on that please. I'm mainly asking about my */boot* partition.
I wanted a seperate boot partition but the boot flag is on / and the /boot partition says it's [I]set for the label.
[/I]here is a screenshot below:
and here is from my menu.lst
```

title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd0,4)
kernel        /vmlinuz-2.6.22-14-generic root=UUID=b23810ae-a9c2-4cf0-9162-5c6ce8e11d32 ro quiet splash
initrd        /initrd.img-2.6.22-14-generic
quiet

```so is this booting from /home or /
Thanks :)

Edit: when I look through the folders it does seem that /boot is where it's booting from, but I'm not sure why it doesn't have the boot flag and is it safe to change that?

---

### Post by logos34 on 2008-02-17
> **seventhc said:**
> when I look through the folders it does seem that /boot is where it's booting from, but I'm not sure why it doesn't have the boot flag and is it safe to change that?

yes, root (hd0,4) = sda5, /boot.  You can safely change the boot flag, but I don't believe it matters to ubuntu

---

### Post by sammydee on 2008-02-17
Don't change the boot flag unless you know exactly what it will do!

Remember, if it ain't broke, don't fix it. If it works fine at the moment, there is no need to change something you may not understand. I've spent many hours messing around with grub, and let me tell you, if it's working, it's best not to touch it at all in case you break it again.

Just my 2 cents.

Sam

EDIT: If I was going to start a brand new partitioning scheme, I would simply use:

swap - 1GB
boot - 500MB
/ - Everything else

Separate partitions look neat, but just end up being a pain when you run out of space on one partition but have loads left on another.

---

### Post by seventhc on 2008-02-17
well the / has 10 gigs, don't think I'll run out of space and having /var and /tmp should speed things up a bit. I also wanted a separate /home partition.
I am constantly trying new systems so for me yo reinstall is no big deal as everything is already backed up on a DVD so it only takes a total of 30 minutes to do a fresh install and have everything back the way I need.
If I do run out of space somewhere then I would change the scheme on next install, which is what this experiment is meant to determine. I think /var and /tmp won't run out, i think it just overwrites old info. I could be wrong, but all part of the experiment. :D

---

### Post by aysiu on 2008-02-17
You don't need a separate /boot, /var, or /tmp partition. A separate /home partition can be nice, though.

---

### Post by sammydee on 2008-02-17
> **seventhc said:**
> well the / has 10 gigs, don't think I'll run out of space and having /var and /tmp should speed things up a bit.

This isn't true unless /tmp and /var are on separate hard disks. Even then, I can't imagine it would make a perceptable difference.

Seriously, one big / partition, or a ten gig / partition and the rest /home is the way to go. I've tried hundreds of partioning schemes and this really is the easiest.

Sam

---

### Post by seventhc on 2008-02-17
> **aysiu said:**
> You don't need a separate /boot, /var, or /tmp partition. A separate /home partition can be nice, though.
I know it's not needed, in the past I've always just let Ubuntu partition for me, but I think I read somewhere having /var and /tmp might speed it up a bit. Not certain of that statements truth/fact/validity, but I figured it couldn't hurt to try. I only tried the separate /boot partition to see if it would speed up boot times. Haven't actually timed it or anything. I was also thinking it might keep things a little more stable.
btw, I did change the boot flag and it does still boot.
Thanks for all the replies everyone. :)
I'll mark it as solved for now. :)

---

