---
title: "mdadm raid 5"
date: 2013-06-12
forum: General Help
---

### Post by beentar on 2013-06-12
Hello, I have a ubuntu system 12.04 and I want to configure a raid 5 with mdadm, I want to know how to get the disk **/dev/sda** which contains the OS in my raid 5 with **/dev/sdb** and **/dev/sdc **! thanks

---

### Post by Cheesemill on 2013-06-12
Backup all of your data.

Reinstall your OS after setting up your RAID5 array using the Live CD.

---

### Post by beentar on 2013-06-12
But I want to configure raid5 with mdadm package.

---

### Post by Cheesemill on 2013-06-12
That's what I'm suggesting you should do. You need to run Ubuntu from a Live CD, then install the mdadm package and set up your array with the 3 drives, then run the installer from the live session and install Ubuntu on to your array.

The array needs to be set up before you install Ubuntu, which is why I suggest to back up all of your data and then do a fresh installation.

---

### Post by beentar on 2013-06-12
thank you cheesemill , can you give me a link or a tutorial on this operation?

---

