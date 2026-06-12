---
title: "Segmentation Fault - Core Dumped in ubuntu 14.04"
date: 2015-12-03
forum: General Help
---

### Post by monkey6 on 2015-12-03
Hello
I have been using Ubuntu 14.04 for last couple weeks (may be month). Today, I have updated a large chunk of softwares and installed a new ram module (4GB extra). 
I have installed Java7 and 8 and upgraded total pc with apt-get upgrade and android studio. Since then I am getting the following error 


     ../../third_party/tcmalloc/chromium/src/free_list.h:118] Memory Corruption detected.
     Segementation Fault (core dumped)


I have tried running firefox, android studio, same problem persist. Aparently, somehow they all have the same error
         
     Core Dumped.


Any idea how to fix memory related issues in ubuntu or how can I go back in a safe zone/period? 
Thanks

---

### Post by deadflowr on 2015-12-03
Moved to ***General Help*** 
as this is not specific to Desktop Environments.

That siad, when you boot up you can access a boot menu, called GRUB.
in GRUB there is should be a setting for memtest.
Run that. (usually best overnight for more verbose results)

To get GRUB, if you do not see it, you need to tap either the shift key or esc key right after the very first screen that usually appears when you turn on the machine.

---

