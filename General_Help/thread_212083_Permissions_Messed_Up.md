---
title: "Permissions Messed Up"
date: 2006-07-09
forum: General Help
---

### Post by rowanparker on 2006-07-09
Hello,
I have my files on a FAT32 partition which is mounted fine and I can read/write/execute. For some reason, I don't own these files, root does in group "plugdev". When ever I try and change the owner it just says "Owner could not be changed". Therefore any time I want to change permissions of a file then I have to do root nautilus which is quite annoying.

How can I solve this?
Thanks, Rowan.

---

### Post by atoponce on 2006-07-09
How are you trying to change the owner?  What command are you using?

---

### Post by rowanparker on 2006-07-09
I was using nautilus and now I just tried chown:```
rowan@hal:~$ sudo chown rowan /home/rowan/docs
chown: changing ownership of `/home/rowan/docs': Operation not permitted
```


Rowan.

---

### Post by Diffusio on 2006-07-09
I have a similar problem. I have a 300gb external hard drive with all my music on it. When I try to delete a song or drag new files onto it, it tells me I don't have the correct permissions.

> Error while copying to "/media/THEBEAST".

You do not have permissions to write this folder.

"THEBEAST" being my external.

---

### Post by taurus on 2006-07-09
How did you mount that partition, by hand or with /etc/fstab?  What does your /etc/fstab look like?
```

more /etc/fstab

```

---

### Post by aysiu on 2006-07-09
You can't *chown* or *chmod* FAT32 partitions.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by rowanparker on 2006-07-09
Thanks, that sorted the permissions out but I still do not own any of the files. Does this matter?

---

### Post by aysiu on 2006-07-09
> **rowanparker said:**
> Thanks, that sorted the permissions out but I still do not own any of the files. Does this matter?
You can never own a Windows partition. The best you can do is make it read/write (FAT32) or read-only (NTFS).

---

### Post by rowanparker on 2006-07-09
OK, Thanks.
I might just make it ext3 and get drivers for use in Windows.

---

