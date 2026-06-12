---
title: "have to reconfigure x on every reboot"
date: 2007-06-23
forum: General Help
---

### Post by Digitallysick on 2007-06-23
I got the latest nvidia driver, but eachtime i reboot it says kernel version doesnt match, i have to run the sudo sh nvidia blah  command and hit yes on everything and type startx to start. How can i fix the kernel version mismatch

---

### Post by jonface on 2007-06-25
I think I got the same problem. Just upgraded to 7.04, installed official nvidia driver, now everytime I reboot X fails to start. I have to reinstall the Nvidia driver, restart gdm. I'll post my logs in about 10 hours when I'm home.

My other comp did this after a clean install but hasn't since I stopped playing with beryl. Anyway, I'll be back soon.

---

### Post by jonface on 2007-06-28
Ok the error I get is:

Error: API mismatch : This NVIDIA driver component has version 100.14.09 but the NVIDIA kernel modules version does not match. Please make sure that the kernel module and all NVIDIA driver components have the same version.

Xorg.log attached. I removed the pci scan stuff to make the file smaller.

Any ideas anyone?

---

### Post by Malviolent on 2007-09-27
I am also having this same problem.

---

