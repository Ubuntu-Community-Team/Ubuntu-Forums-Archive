---
title: "freeze after process have taken all my RAM"
date: 2020-12-06
forum: General Help
---

### Post by adosi on 2020-12-06
Always when i mount drive (the longest freeze) process take all my RAM and pc is completely unresponsive (only mouse can be moved but that's it) until the process finishes sometimes 5 min, then it work normal. I have 32Gb ram in my omen 15 and using Ubuntu 20.04 LTS. I have tried appending vm.swappiness=5 and vm.min_free_kbytes=65536 to /etc/sysctl.conf but it haven't worked. Any suggestions ? thank you.

---

### Post by Impavidus on 2020-12-07
What drive do you mount and how do you mount it? What application uses your ram? With more than 8GB ram, very few applications are capable of filling all of it.

---

### Post by adosi on 2020-12-07
tried mount it using terminal, command mount and also several gui file managers (and default for ubuntu)

---

### Post by Impavidus on 2020-12-08
What drive? Size, type of filesystem? Encrypted?

What was the exact command you used to mount it? What's the name of the process taking all your memory? It appears from the plot of memory usage that some process slowly consumes all ram and swap, then terminates.

---

