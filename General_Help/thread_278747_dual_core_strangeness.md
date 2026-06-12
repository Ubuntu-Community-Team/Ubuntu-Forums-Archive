---
title: "dual core strangeness"
date: 2006-10-16
forum: General Help
---

### Post by linuxnoob40 on 2006-10-16
i sucesfully installed the smp kernel for my dual core processer however it seems like it runs slower than it did before in games i have a lower frame rate and i have no way to set the affinity of the cores to make 1 do 1 thing and the other work on something else. have i done something wrong? is there another step to this? or should i just go back to the old kernel and be happy with a bleeding fast machine working as 1 core instead of 2 ?

---

### Post by bettlebrox on 2006-10-16
What kernel version are you using?

In theory a dual-core should be faster, but this tends to only be true with multi-threaded application (such as a webserver serving up pages to multiple users). With single threaded apps (like most current games) dual-cores or HT can be slower.

Try running top while a game is running to see if anything else is using up CPU?

I thought I remember reading, a while back, that there may be issues with the graphic-card drivers and SMP kernels. U using NVidia?

---

### Post by linuxnoob40 on 2006-10-16
im using the one for amd k7 smp and yes i have a nvidia card. i dunno the whole system seemed slower it lagged alot so i booted back to the old kernel and things are good again. just find it odd i guess

---

### Post by bettlebrox on 2006-10-17
What is the output of "uname -a". Maybe your running an older kernel? Also, which verion of Ubuntu are you running?

---

