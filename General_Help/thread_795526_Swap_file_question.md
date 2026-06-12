---
title: "Swap file question"
date: 2008-05-15
forum: General Help
---

### Post by noiseordinance on 2008-05-15
I have conky running on my desktop and one of the things it displays is my swap file usage. For whatever reason, I made my swap file to be double my 2GB of RAM, so my swap is 4GB, which apparently is huge. I've never seen the swap file even be used or so much as twitch. Is this normal? Should I shrink the size of it and give it to root? Is that even possible?

---

### Post by oilchangeguy on 2008-05-15
> **noiseordinance said:**
> I have conky running on my desktop and one of the things it displays is my swap file usage. For whatever reason, I made my swap file to be double my 2GB of RAM, so my swap is 4GB, which apparently is huge. I've never seen the swap file even be used or so much as twitch. Is this normal? Should I shrink the size of it and give it to root? Is that even possible?

yes, shrink your swap to 512mb. swap is virtual ram. and with 2gb, you do not need 4gb of virtual ram.

---

### Post by noiseordinance on 2008-05-15
That's kinda what I figured... how do I shrink the partition without hosing my / and /home partitions? What size should I make it?

---

### Post by Steveway on 2008-05-15
> **oilchangeguy said:**
> yes, shrink your swap to 512mb. swap is virtual ram. and with 2gb, you do not need 4gb of virtual ram.

But if you want to suspend to disk then you should use a swap-partition of about 1.5 to 2 or more times the amount of RAM you have.

---

### Post by oilchangeguy on 2008-05-15
> **Steveway said:**
> But if you want to suspend to disk then you should use a swap-partition of about 1.5 to 2 or more times the amount of RAM you have.

i disagree. 2gb of physical ram is plenty. virtual ram is not needed.

---

### Post by noiseordinance on 2008-05-15
should i just do 1gb of swap to be safe? i don't really need the space THAT bad. i just saw an article on installing gparted to resize. is that recommended?

---

### Post by oilchangeguy on 2008-05-15
> **noiseordinance said:**
> should i just do 1gb of swap to be safe? i don't really need the space THAT bad. i just saw an article on installing gparted to resize. is that recommended?

my suggestion would to use 512mb. and next time you install ubuntu, let it set it's own partitions.

---

### Post by noiseordinance on 2008-05-15
well, i was told by other sources that by having /home on a separate partition, it's easier to install newer versions of ubuntu in the future. i used the advice of several people on this forum to do the partition layout and sizes that i came up with.

thanks.

---

