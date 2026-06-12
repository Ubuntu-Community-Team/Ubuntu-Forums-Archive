---
title: "Locallly installed ubuntu desktop consuming too much memory."
date: 2013-10-14
forum: General Help
---

### Post by chetanmadaan on 2013-10-14
Hi -

My Locally installed Ubuntu 12 started to slow down last week and i added another 4 GB ram to the second slot... restarted and it worked fine (previous i was only using 2 GB).

Now, this week again... the memory issue.

here's the current memory

```
Last login: Thu Oct 10 20:25:37 2013 from 192.168.1.18
root@homeub:~# free -m
             total       used       free     shared    buffers     cached
Mem:          5878       5718        160          0        696       3877
-/+ buffers/cache:       1143       4734
Swap:         1954         30       1924
root@homeub:~#
```

You can see that out of 6 GB... only small amount of memory is available... we are not using this server to host an actual site or something... the server is being used for running local projects (php, Mysql, Apache) by around 5 - 10 people at a time.

Any tips on how i can get the memory issue fixed?

Thanks
Chetan

---

### Post by grahammechanical on 2013-10-14
Look at the amount of cached memory - 3877. This is memory held in reserved. So, there is plenty of memory available. Think of this as ready to use memory. Run this command and see what is actually using the memory.

```
top
```

[http://askubuntu.com/questions/80133/why-is-the-cache-in-my-memory-always-full](http://askubuntu.com/questions/80133/why-is-the-cache-in-my-memory-always-full)

Regards.

---

### Post by chetanmadaan on 2013-10-14
alright... now i see it. top brings up utserver (utorrent server i installed last week)... didn't realize it would consume that much memory.

Thanks anyways.

---

