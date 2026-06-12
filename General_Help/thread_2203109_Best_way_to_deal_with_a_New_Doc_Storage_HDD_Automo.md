---
title: "Best way to deal with a New Doc Storage HDD? Automount??"
date: 2014-02-01
forum: General Help
---

### Post by 777funk on 2014-02-01
I'm still learning the ropes with linux. I just got a new 3TB HDD. What's the best way to use this for document storage. Is Automounting a good idea? This will be shared with Windows. I'm also curious of the fastest way to use this drive. It's formatted NTFS so that I can also access the data from Windows. 

But that said (and on another note) I had to use 2 partitions (one 746GB which is the max XP wanted to pickup and one 2TB which is invisible in Windows but works in linux) so would there be an advantage to NOT use NTFS for the Linux only partition? I sure wish I could get Win XP to see both partitions but for some reason the second 2TB partion isn't showing up.

---

### Post by Erik1984 on 2014-02-01
Yes there is an advantage: with ext4 as the file system you can keep the permissions on your files correct and Linux can perform checks and repairs. A possible downside is that those files are unreadable by default in Windows so you have to use 3rd party software to view them in case you have to use Windows and need those files.

---

### Post by 777funk on 2014-02-01
So is Automount the best way for the new drive partition(s) to become  part of the Linux OS for calling on files in the day to day?

---

### Post by Erik1984 on 2014-02-02
If you need those files frequently then yes automounting (I guess you mean putting a line in /etc/fstab for the linux partion of the storage HDD) is most convenient.

---

