---
title: "GRUB question"
date: 2007-06-22
forum: General Help
---

### Post by s_h_a_d_o_w_s on 2007-06-22
How can i "refresh" the grub list when i boot my computer, i have deleted some partitions and i want to shorten the list to choose from. :D

---

### Post by logos34 on 2007-06-22
Remove them from /boot/grub/menu.lst or comment them out by putting a hash '#' mark at the beginning of each line of the entry

Run 
sudo update-grub

---

### Post by s_h_a_d_o_w_s on 2007-06-23
Oh my gosh thank you very much!

:D

---

