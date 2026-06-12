---
title: "jfs problem"
date: 2005-07-28
forum: General Help
---

### Post by stiivi on 2005-07-28
I am experiencing JFS mount problems with theLive CD. I have a JFS (extended) partition on my laptop which is /dev/hda6 on my installed mandrake system. In the Ubuntu Live CD cfdisk detects that partition as JFS too, however when I (su)do:

> mkdir /mnt/disk
> mount -t jfs /dev/hda6 /mnt/disk

i get an error about bad fs type or bad superblock.

in my mandrake /etc/fstab I have:
...
/dev/hda6 /home jfs noatime 1 2
...

Where the problem should be?

Thanks.

---

### Post by shangouet on 2005-08-13
Hello,
Same problem for me.
I'm on Ubuntu Hoary and I created a new partition for data (to replace my no-longer-used windows part ;-)):

sudo mkfs.jfs /dev/hda1

Then, I try to mount it with this command:

sudo mount -t jfs /dev/hda1 /mnt/data

The following error message occurs:

mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Do I missed something ?
Thanks.

---

### Post by thor on 2005-08-19
It could be because you did not cleanly unmounted your jfs filesystem last time.

To fix this problem, boot your LiveCD, then try:

jfs_fsck /dev/hda1

This should replay filesystem's journal and make filesystem clean. Then you should be able to mount it with mount -t jfs /dev/hda1 /mnt

---

### Post by stiivi on 2005-08-20
Thanks! This was the problem: I was suspending my Mandrake, therefore the jfs file system was not clean. I had to shut down it first, then it worked.

Now I am happy new Ubuntu user - installed just yesterday evening. :)

---

