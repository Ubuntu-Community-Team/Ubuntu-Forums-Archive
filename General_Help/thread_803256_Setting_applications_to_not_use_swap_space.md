---
title: "Setting applications to not use swap space"
date: 2008-05-22
forum: General Help
---

### Post by rm-rf on 2008-05-22
I'm running a virtual windows xp via vmplayer. It runs fine enough, but from time to time and after it has been sitting idle for a while it becomes dog slow. My guess is that while not in use, linux simply sends the application to swap memory.

Question; is there a way to configure Linux as to not use swap memory for certain applications?

Thanks in advance, take care

- rm-rf

---

### Post by chrisccoulson on 2008-05-22
You can't stop an application from using swap if it runs out of physical RAM, but you can change the preference for swapping out pages versus freeing up physical RAM by getting rid of cache - by adjusting the 'swappiness' value. A swappiness of 0 will mean the kernel will always get rid of cache to free up RAM (when it can) as opposed to swapping out pages. A value of 100 will do the opposite (pages will always get swapped out).

To test a swappiness of 0:
```
sudo sysctl vm.swappiness=0
sudo swapoff -a
sudo swapon -a
```

To make it permanent, edit your /etc/sysctl.conf and add the following line to the bottom of it:
```
vm.swappiness=0
```

---

