---
title: "Ubuntu doesnt start? - Didnt change partition table or Grub?"
date: 2007-08-29
forum: General Help
---

### Post by muhu on 2007-08-29
Hello

I dont know why but I cant load my ubuntu partition. I didnt chang something with the partitions or with grub. If i want to start ubuntu on the left corner the message "GRUB" appears. This suddenly appeared and I have no explanation why? What can I do? Before that I worked just normally with ubuntu and only installed a few things  with apt-get but didnt change system things.

thx

---

### Post by MoLE on 2007-09-06
What sort of error do you get when you try to load your ubuntu partition?  Can you give us some idea of what your /boot/grub/menu.lst looks like?

---

### Post by Warren Watts on 2007-09-06
There was a kernel update the other day that re-wrote menu.lst.  It's a possibility that the upgrade is responsible.  The update edited my menu.lst file and completely removed two entries I had in there for other OS's.

I am running Ubuntu on two machines, and when I noticed the other machine notifying me that updates were available, I went in and created a backup of the menu.lst file before I installed the update.  After the update was complete, I went and looked, and my menu.lst file had been re-written. It didn't do anything odd on the other machine though, and my backup wasn't needed.

Assuming you haven't edited the menu.lst file yet, check and see what the date is on the file.  And of course, post it here like the previous posted suggested... :-)

---

