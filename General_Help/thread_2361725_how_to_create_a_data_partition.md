---
title: "how to create a data partition"
date: 2017-05-20
forum: General Help
---

### Post by zandu on 2017-05-20
Hi am running ubuntu  16.04 xfce and I want to create a data partition that would have read and write permissions what is the simplest way to do it .

---

### Post by LastDino on 2017-05-20
Is your data partition needs to be accessible by Windows too? What partition scheme you have at the moment? How much space do you want to allocate?

If you know how to make the partition with Gparted and it does not need to be accessible by Windows, I would use "ext4", if it needs to be accessible by windows I would use NTFS

Then all you need to do is run a simple command to have read write permissions, generally you don't need to.

---

### Post by zandu on 2017-05-20
It dosent need to be accessible to windows so I will make it ext4

---

### Post by LastDino on 2017-05-20
Okay, after you're done with making partition, let me know here if you do not have read write permissions. Generally you will have, just in case if you don't post here.

---

### Post by oldfred on 2017-05-20
I like to have multiple installs, most testing something, but want all my data in all of them so I can find my notes, use my standard bookmarks, and see email.

More details on setting up a shared data partition including mounting, permissions & ownership & linking data back.

 Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /mnt/data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /mnt/data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by zandu on 2017-05-20
> **LastDino said:**
> Okay, after you're done with making partition, let me know here if you do not have read write permissions. Generally you will have, just in case if you don't post here.

Hi  I have created a partition but it does not have read write permission  seems gparted has made it root . I deleted the partition an re did it but it still is the same

---

### Post by oldfred on 2017-05-20
As posted above, chown & chmod commands:
[https://ubuntuforums.org/showthread.php?t=1811198&p=11081384#post11081384](https://ubuntuforums.org/showthread.php?t=1811198&p=11081384#post11081384)

---

