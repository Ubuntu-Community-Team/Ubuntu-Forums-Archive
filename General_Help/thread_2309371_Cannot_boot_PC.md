---
title: "Cannot boot PC"
date: 2016-01-09
forum: General Help
---

### Post by Earl_tom on 2016-01-09
When I turn my pc on all I see is GNU GRUB version 2.02~beta2-9ubuntu1.7

There is one option called "UNetbootin"

When I select it I get 

"error : file '/boot/ubnkern' not found."

I am freaking out, is this the end of my computer? I can no longer boot into windows or linux mint D: I am about to cry.

[https://youtu.be/qBDVDaaxh2E](https://youtu.be/qBDVDaaxh2E)

---

### Post by Earl_tom on 2016-01-10
Holy crap...

I think the gods blessed me while searching stuff up on Google on how I might be able to fix this problem.

[https://www.linux.com/learn/tutorials/776643-how-to-rescue-a-non-booting-grub-2-on-linux/](https://www.linux.com/learn/tutorials/776643-how-to-rescue-a-non-booting-grub-2-on-linux/)

I followed all the steps and this was my solution. I now have my normal GNU GRUB screen back. I think what caused this problem was that I was using UNetbootin on linux and used the options Diskimage:ISO, Type: Hard Disk, I then pressed ok and while it was doing what it does, my linux partition ran out of memory, then I no longer had Xauthorization. Then I had what I posted in the video. I guess this has taught me my lesson. I will be more careful.

---

