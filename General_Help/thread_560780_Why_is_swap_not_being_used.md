---
title: "Why is swap not being used?"
date: 2007-09-26
forum: General Help
---

### Post by Mamsaac on 2007-09-26
I don't complain, for the fact I don't really need it (2gb of ram and I'm using only around 260mb-360 when I'm using everything), but for curiosity, is there an explanation?

I tried swapon and:

> mamsaac@mamsaac-laptop:~$ sudo swapon -a
swapon: /dev/disk/by-uuid/7e2bc205-412b-402f-a853-071296eb6a14: Dispositivo ó recurso ocupado


Where that stands for: "Device or resources busy" (resources is probably not the best translation for this case).

It appears mounted on gparted. Here's an image of my system monitor attached. 

Thanks in advance :)

---

### Post by bodhi.zazen on 2007-09-26
The more ram you have the less swap you will use.

You can get a better look from the terminal with these commands :

```
free
```This will show your memory usage

```
mount
```This will show your mounted partitions, including swap.

---

### Post by ddrichardson on 2007-09-26
What's the output of /etc/fstab?

---

### Post by rsambuca on 2007-09-26
You are only using 257MB of your 2GB Ram, so of course it won't touch the Swap!  Swap is much slower than RAM, so be thankful that you aren't using it!  Frankly, with 2GB ram, I doubt you will ever use the swap unless you are doing some very memory intensive stuff.

---

### Post by ddrichardson on 2007-09-26
I misread this post. Your swap won't be used unless you're doing some intensive use. If mount shows the swap partition as mounted, then the swapon is most likely reporting device busy because it's already swapon.

---

### Post by Mamsaac on 2007-09-26
That's what I thought for a second... but since I'm not an expert at all, I had to ask the question. Thanks so much for this many replies :)

---

