---
title: "Preallocate memory for Ubuntu?"
date: 2008-04-28
forum: General Help
---

### Post by pAt84 on 2008-04-28
Hi,

I hope that is the right forum to ask this question. I am a little unsure.

I am using Matlab and C++ to do certain things which now and then involve the computation of huge arrays (matrices). My machine has 4 GB of memory. However, sometimes it happens that my arrays are actually larger than this. Ubuntu then moves a part to the swap file. The thing is that when this happens my system gets horribly slow because also parts of the OS itself land in the swap. Is there a way to force a few hundred MB to stay free, so the OS can always run smoothly?

Thanks,
Pat

---

### Post by ryanhaigh on 2008-04-28
I have also found the system to run slowly after running a huge app because parts that are usually in memory are swapped out. AFTER running the application and exiting to get the system back up to speed I use:
```

sudo swapoff
#wait for that to finish
sudo swapon /dev/sd** #where sd** is your swap partition

```
After that everything gets back to normal. I know this isn't exactly what you want as it isn't useful WHILE running the app but it will get you back up to speed afterwards.

---

### Post by pAt84 on 2008-04-29
Thanks. It does not really help though. There must be a way to reserve some memory to the system.

Pat

---

