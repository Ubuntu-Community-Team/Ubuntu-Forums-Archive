---
title: "Resizing partitions"
date: 2008-02-03
forum: General Help
---

### Post by lukataylo on 2008-02-03
hey guys i am a Linux noob, just installed Ubuntu an i foolishly made the Ubuntu partition bigger  so

here are my partitions: On a 150 gig drive

windows xp pro: 41.1
Ubuntu: 105 gig

i would like to make the xp partition bigger, i have got a Ubuntu live CD which has g parted on it.

Please anyone give me a step by step guide on how to do that, and please tell me what is an optimal size of an Ubuntu partition.

Thanks all

---

### Post by forestpixie on 2008-02-03
boot the livecd - run parted from there

assuming that the ubunut partition directly follows the xp one - resize the ubunut partition, then apply that wait for it to complete - I think that you have to resize and then move the ubunut partition to the right (or left depending where xp is) so that the freespace is next to the xp one then you can resize the xp partition 

wouldn't think there's an optimal size depends what you want to do with it

if you're not going to be storing data in the ubuntu partition maybe 15 or 20 Gb

The other way to address the problem could be to resize the ubuntu partition and then make a shared partition that both can use

---

### Post by jan quark on 2008-02-03
some links

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)


[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

---

### Post by lukataylo on 2008-02-05
Hi guys thanks for that but didn't work when i try to resize the Ubuntu partition it comes up with an error

---

### Post by bodhi.zazen on 2008-02-05
can you post the error ?

My guess would be that the partition is mounted.

---

### Post by lukataylo on 2008-02-06
sorry for the late reply i can't post the error yet as i just landed the ubuntu cd to a friend but it was not mounted i unmounted it

---

### Post by sandysandy on 2008-02-06
u can try downloading gparted from the net and burn a CD. Use the gparted CD to boot the computer. once the computer boots using gparted CD, the partitions are visible on the open  window. The partitions can be resized by simply dragging and resizing.

regards

---

