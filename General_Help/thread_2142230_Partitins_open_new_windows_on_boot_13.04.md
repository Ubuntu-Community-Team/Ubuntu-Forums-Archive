---
title: "Partitins open new windows on boot 13.04"
date: 2013-05-05
forum: General Help
---

### Post by spiky001 on 2013-05-05
Hi

I have switched to 13.04 and have an annoying problem, when I boot into 13.04 I get 6 partitons moutning and opening new seperate windows which I have to close before I can do anything on laptop? They all appear in the side panel ok which they did in earlier versions, but then 6 of them open a nautilus window, there are more than 6 partitions on the laptop. I have checked /etc/fstab nothing in there to mount them, I have installed configuration editor but cant find any setting in there.

---

### Post by carl4926 on 2013-05-05
Create a new user and see if the problem exists there

---

### Post by spiky001 on 2013-05-05
Hi

Ok problem resolved I found out it was a late mounting usb drive. So the system would boot then the drive got mounted, thinking it had been inserted opening it in nautilus.

---

