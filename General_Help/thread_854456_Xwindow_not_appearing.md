---
title: "Xwindow not appearing"
date: 2008-07-09
forum: General Help
---

### Post by satheesan on 2008-07-09
I have a Dell Dimension E520 with intel Core2 Duo Processor Desktop. It has got Integrated Intel Graphics Accelerator X300 and 19" Ultrasharp Flat panel Monitor. 
I had installed Ubuntu 7.10 and was working without any problem. Recently uograded to Ubuntu 8.04 - Hardy Heron. Now the X window is not coming sometimes (and it comes some other times). Please help me to solve this problem. I have Gnome
Thanks and Regards
Satheesan

---

### Post by unoodles on 2008-07-09
There are two things you could try. First you could get to a terminal and type sudo dpkg-reconfigure -phigh xserver-xorg
A more "user-friendly" way would be to boot into recovery mode and choose the option "Fix X-Server".

---

### Post by satheesan on 2008-07-13
Thank you for your reply. It solved my problem

---

