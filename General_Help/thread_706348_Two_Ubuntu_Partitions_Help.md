---
title: "Two Ubuntu Partitions Help"
date: 2008-02-24
forum: General Help
---

### Post by realGaurab on 2008-02-24
Ok, this is something that happened. I had ubuntu installed in my comptuer. Then I installed another ubuntu partition in the same hard disk. When installing the new partition, it asked me if I wanted to save my documents and settings. I said yes, but the only thing that looks to have been selected is the firefox bookmarks. Nothing else is saved. 

Anyway, I know the previous partition is still in the disk because now the hard drive space that ubuntu says is the total size minus previous partition size. So I know the data I had must still in in the disk. My question is how can I copy the data from the previous partition to this new one, and when I'm done transferring them here, then delete that partition so this partition uses the entire disk?

---

### Post by logos34 on 2008-02-24
Simply mount both partitions from the ubuntu live cd and copy the files to your new root partition.  Unmount both.  Then use gparted (system>admin>partition) to delete the old root and expand the new one (left?) into the empty space.  (Note: resizing a partition to the left takes a while).

---

### Post by realGaurab on 2008-02-24
I booted with live CD. I can see both the partitions. But the problem now is I cannot copy from the old partition to the new one. When I copy, the 'paste' option is greyed out in the new partition. When I drag into the new partition, it says 'you don't have necessary permissions'. I can't seem to get to the partitions using the shell. Can you please help me out here. Thanks.

---

### Post by logos34 on 2008-02-24
open the file browser as root:

**gksudo nautilus**

or mount them manually:
[B]
sudo mkdir /mnt/ubuntu_old

sudo mkdir /mnt/ubuntu_new[/B]

**sudo mount -t ext3 /dev/sda1 /mnt/ubuntu_old** (--> replace sda1 with your actual root)

**sudo mount -t ext3 /dev/<newroot> /mnt/ubuntu_new**

If unsure post your partition list:

**sudo fdisk -l**

---

### Post by realGaurab on 2008-02-24
I created two mounts. But still, I cannot copy files from one to another. It still gives me the same 'no permission' message. I am still in live session. 

[url=http://img261.imageshack.us/my.php?image=screenshotin8.png]
Screenshot of GParted.


Edit: Nevermind. I should have done it as my primary user instead from the live CD. I can now copy everything from my old partition to my new one. Thanks. However, I might need help combining the partitions so that this new one uses the whole disk. I can get rid of the old one when I am done copy some files.

---

### Post by logos34 on 2008-02-24
> **realGaurab said:**
> I should have done it as my primary user instead from the live CD. I can now copy everything from my old partition to my new one. Thanks. However, I might need help combining the partitions so that this new one uses the whole disk. I can get rid of the old one when I am done copy some files.

Oh, I thought you couldn't see it/wasn't showing the whole disk space.

You don't 'combine' or merge two partitions.  Just delete the old root and grow the new ubuntu into the resulting unallocated space. (again, use the live cd because root cannot be mounted when resizing)

---

