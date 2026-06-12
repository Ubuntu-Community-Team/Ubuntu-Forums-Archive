---
title: "Not being able to mount a partition as NTFS."
date: 2013-08-27
forum: General Help
---

### Post by axy-david on 2013-08-27
Hello,
So I mistakenly made a NTFS partition as linux-swap, I fixed that and   now the partition is fully functional in windows, but when I check with   GParted it still detects it as a linux-swap type. What can I do  to  mount that partition as NTFS?
Can I force mount it or is there any other way?
I already tried to change the partition type from terminal, it said it succeeded but it still detects it as a linux-swap.

---

### Post by axy-david on 2013-08-27
nevermind I found [http://karelzak.blogspot.dk/2009/11/wipefs8.html](http://karelzak.blogspot.dk/2009/11/wipefs8.html)
It seems I had 2 filesystems on that partition and i removed the linux-swap one

---

### Post by steeldriver on 2013-08-27
Well that's a bit of a puzzle. Can we see the results of the following terminal commands please?

```

sudo parted /dev/sdXX print

sudo file -sL /dev/sdXX

swapon -s

```

where /dev/sdXX is the actual partition (/dev/sda7 or whatever). How did you fix the original mistake?

---

