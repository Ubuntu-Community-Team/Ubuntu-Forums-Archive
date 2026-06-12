---
title: "unable to mount ext4 partition"
date: 2014-09-13
forum: General Help
---

### Post by joe135 on 2014-09-13
Hi all, I am new to Ubuntu coming from Fedora, and am trying to mount a partition with the **mount** command, but I am having trouble doing so.    **fdisk -l** tells me:

```
/dev/sda3       976900096  1953523054   488311479+  83  Linux
```

and **blkid** tells me:

```
/dev/sda3: LABEL="Data" UUID="e8fb3090-35d5-4b2b-884b-7b7065f60332" TYPE="ext4" 
```

so, I presume I need to type something like this:

**sudo mount -t ext4 -U e8fb3090-35d5-4b2b-884b-7b7065f60332 /mnt/Data Data**

However, this doesn't work.   Eventually I want to add this partition to /etc/fstab, and I figure once I get it to mount manually I'll be able to do so.   Can anyone tell me what I'm doing wrong?    Thanks.

---

### Post by deadflowr on 2014-09-13
Did you make a directory in /mnt called Data? 

(And I don't know what the second Data is suppose to be.)

---

### Post by joe135 on 2014-09-13
I did have a directory called /mnt/Data, but the field after /mnt/Data that you said you weren't sure about what it was for, was the culprit.   I removed it and mounted the partition with no problem.    Thanks!

---

