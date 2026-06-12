---
title: "Cannot login as personal user after redistributing free space between partitions"
date: 2013-04-26
forum: General Help
---

### Post by cancelliere on 2013-04-26
I've recently run out of space on my root partition, so I've moved 4 GB of free space from /home partition to root. After that I can't login as my user anymore, but only as guest. At login, if I try to use my user, the system acknowledges the password but it suddenly shows a black screen with white lines which all end saying "OK". I can't tell more about these lines because they disappear soon after. 
The only way I can use my PC now is to login as guest, therefore I cannot even use the terminal to find out more. Moreover, I've tried to mount my partition loading the LiveCD, but it fails not showing any error. 

I use Version 12.04 (precise) 32 bit Kernel Linux 3.2.0-37-generic-pae GNOME 3.4.2

---

### Post by ajgreeny on 2013-04-26
How did you carry out the partition changes and what exactly did you do?

---

### Post by cancelliere on 2013-04-26
I used gparted from the liveCD to move 4 GB from my /dev/sda3 partition, which is my user's home, to my /dev/sda1, which is root.

---

### Post by cancelliere on 2013-04-26
May this be a problem with the UUID of the partition?

---

### Post by cancelliere on 2013-04-27
I've solved by updating Grub. I've followed [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing) at the section "Via ChRoot"

---

