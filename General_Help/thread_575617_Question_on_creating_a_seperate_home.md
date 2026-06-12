---
title: "Question on creating a seperate /home"
date: 2007-10-14
forum: General Help
---

### Post by dpar on 2007-10-14
I tried to creat a seperate /home using [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome).
Everything would have probably gone well, except that I couldn't use a LiveCD because they kept mounting the partitions.
I finally used a Gparted LiveCD and 'goterdone':)
Here was the problem: I never noticed, but gparted formated the new partion as ext2
I screwed up the fstab editing by inserting ext3 instead of ext2 and couldn't boot ubuntu.
Anyway,I managed to edit fstab to say ext2 and get in.

After all this rambling, here's my question.....Is there any problem leaving the partition as ext2???

---

### Post by r-mo on 2007-10-14
No problem with leaving it as ext2,  ext3 is just ext2 with journaling.  You can however convert the filesystem to ext3 very easily.

* Open up a terminal.
* sudo su -
* umount /dev/sda2 (or whatever it is)
* tune2fs -j /dev/sda2
* nano /etc/fstab  and change the ext2 to ext3
* mount /dev/sda2

---

### Post by dpar on 2007-10-14
Thank you......I assume that this will not mess with any data on the partition?
Just convert to a journalized partition, right?

---

### Post by dpar on 2007-10-14
Does anyoneknow if tune2fs will mess with any data on the partition???I don't want to lose anything[-o<

---

