---
title: "[Ubuntu 15.10]Swappiness"
date: 2015-11-10
forum: General Help
---

### Post by Lucas_Winther on 2015-11-10
Hello. I have installed ubuntu on a custom built computer. On it is 3 gigabyte of ram, and therefore i want to lower the swappiness to something lower. Lets for example say 10. How do i do this in the newest ubuntu?

I've read that you should edit /etc/sysctl.conf;  But when i try nothing about swappines is showing.

Any and all help appreciated - Lucas

---

### Post by oldos2er on 2015-11-10
Nothing about swappiness is there by default; add it to the end of the file: ```
vm.swappiness=10
``` ```
source /etc/sysctl.conf
``` will activate the change.

---

### Post by Lucas_Winther on 2015-11-11
Thank you very much. I thought it was a value you swapped, not one you made :D

---

