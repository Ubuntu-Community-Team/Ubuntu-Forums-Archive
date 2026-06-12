---
title: "Copying Ubuntu install to new HDD?"
date: 2008-03-08
forum: General Help
---

### Post by chazdraves on 2008-03-08
Well, I know there are a few threads on this, but I found them a bit too deep, and I'd like to start my own. Here are the facts:

I have a wonderfully-functional install of 7.10 that I don't want to re-do
I have a new/blank WD Raptor that I would like to be running off of
I have a LiveCD for GParted
I tried copying my partition from one HDD to the other (took over 30 minutes) and it doesn't boot, doesn't do anything.

Can someone give me a hand here?

Thanks, all!
- Chaz

---

### Post by dcstar on 2008-03-09
> **chazdraves said:**
> Well, I know there are a few threads on this, but I found them a bit too deep, and I'd like to start my own. Here are the facts:

I have a wonderfully-functional install of 7.10 that I don't want to re-do
I have a new/blank WD Raptor that I would like to be running off of
I have a LiveCD for GParted
I tried copying my partition from one HDD to the other (took over 30 minutes) and it doesn't boot, doesn't do anything.


Do a search for restoring Grub, you need to do that after copying the partition to a drive without a boot loader.

---

### Post by chazdraves on 2008-03-09
That being said... What if I install Ubuntu on the new drive and then copy that partition over? The install should configure Grub... and the copy should dump in everything I need, right?

- Chaz

---

### Post by Yellow Pasque on 2008-03-09
How are you copying the partition? With dd? You should probably look into dd if you have not already. I copied my Arch Linux install from a 4200RPM 40GB drive to a 5400RPM 40GB drive and booted it right up.

---

### Post by chazdraves on 2008-03-09
No, not with any command. I'm using GParted (which I believe is simply dd, right?). I think the data's all there, but GRUB must be missing because it won't boot. Although, it doesn't show up in the file manager either...

- Chaz

---

### Post by astrotech226 on 2008-03-09
> **chazdraves said:**
> No, not with any command. I'm using GParted (which I believe is simply dd, right?). I think the data's all there, but GRUB must be missing because it won't boot. Although, it doesn't show up in the file manager either...

- Chaz

If you have the OS and data copied, you just need to copy the master boot record using dd.  Change the device names to match, but like this:

```
dd if=/dev/sda of=/dev/sdb bs=512 count=1
```

---

### Post by Lemons on 2008-03-09
I am also having some difficultys copying my installation over and getting it to boot. I got it on the other hard drive fine using gParted (Im on it right now), but when I try to make this hard drive the first priority for booting, it wont work... I am trying to see what super grub can do (I tried it once, just shifted around my old HDDs grub menu... Not what I really wanted). Is there anything I have to go and change manually?

Thanks,
~Kris

---

