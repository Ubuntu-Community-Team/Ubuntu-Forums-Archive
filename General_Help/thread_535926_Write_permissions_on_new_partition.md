---
title: "Write permissions on new partition"
date: 2007-08-27
forum: General Help
---

### Post by Zef_ on 2007-08-27
Hmm well, made a partition in the free space at the end of my drive and it shows up as a disk. It's formatted as ext3, but I just don't have the permissions to actually use it. The only thing on it is a lost+found folder which I can't access.

Forum search did not help, surprisingly. So any help you can lend in order to be able to use that partition will be nice.

---

### Post by tzulberti on 2007-08-27
You should edit the /etc/fstab file and put the words "rw,user"  so a normal user can write in that partition.

---

### Post by Zef_ on 2007-08-27
It doesn't look like my fstab has an entry for that partition, even though it is mounted. There are options for changing the permissions using the properties window in the gui... Couldn't I log in as root and do it that way?

---

### Post by Zef_ on 2007-08-27
Ok I solved it - needed to go to terminal and change ownership by typing 'sudo chown myusername /media/disk' where media/disk is the mount point of the disk. So it was owned by root before, whereas now its owned by me. That's also why it didn't show up in my fstab file, because the owner was root.

---

### Post by Digram_seth on 2007-08-27
thanks i was having the same problem today

---

### Post by ZED RINO on 2008-02-07
Hello,
Is there a way yo manage all that with a graphic tool ?
Thanks

---

