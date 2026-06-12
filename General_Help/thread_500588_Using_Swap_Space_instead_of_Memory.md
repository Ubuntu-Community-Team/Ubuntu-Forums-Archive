---
title: "Using Swap Space instead of Memory"
date: 2007-07-14
forum: General Help
---

### Post by ergjoop3 on 2007-07-14
Hi,
     I have a computer with 1 GB of memory. However, I need to run a program that requires about 3 - 4 GB of memory space. Whenever I run this program, I get an SIGSEV segmentation fault as the memory usage rises to 98% before starting to use my 4 GB swap partition.
     Is there any way for me to force the system to start using swap when, say, 80% of the memory is full? Is this advisable?

Thanks.

---

### Post by benerivo on 2007-07-14
I know you can change the 'swappiness' of linux, so that it will tend to use the swap space more or less depending on what this has been set at. I believe the deafult value is 60 (out of 100). I have 750MB and don't run that many memory intensive programs so i have changed the swappiness to 10 so that it wil use the ram more, and the swap space less - making it operate slightly faster.
You can change the value - i would reccommend trying 90 to see if it works - by editing the /etc/systctl.conf file to include this line directly underneath the "kernel.printk = 4 4 1 7" entry (about 10 lines down)...

vm.swappiness=90

Then reboot.

---

