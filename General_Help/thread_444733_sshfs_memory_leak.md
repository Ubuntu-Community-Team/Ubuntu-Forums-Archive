---
title: "sshfs memory leak?"
date: 2007-05-15
forum: General Help
---

### Post by mbradlcu on 2007-05-15
Hi folks,
my system is exhibiting the following strange behavior when mounting Linux or osx boxes using sshfs.
After a day or so I find my machine's memory and swap almost all used up and the system performance is almost non responsive. here's the top output:
Mem:   1028116k total,  1017296k used,    10820k free,     2668k buffers
Swap:  3004112k total,  2148368k used,   855744k free,   102052k cached

it only happens if I mount another machine using sshfs. To remedy the problem I have to unmount the dirs and do 'swapoff -a' wait, wait, wait,, then 'swapon -a'. My machine returns to normal operation, here's the output after:
Mem:   1028116k total,  1017332k used,    10784k free,     7232k buffers
Swap:  3004112k total,     1468k used,  3002644k free,    83912k cached

Anyone have any suggestions on how to diagnose this issue any further?
thanks in advance!

---

