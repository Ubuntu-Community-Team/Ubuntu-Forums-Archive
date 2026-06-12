---
title: "getting error &quot;failed to mount /media/ssd&quot;"
date: 2022-03-19
forum: General Help
---

### Post by ravsmith82 on 2022-03-19
I am new to this. i have setup partition and mount it. it went well so far but when i restart the machine i get:
[HTML][196.271891] EXT4-fs (sda1): Unrecognized mount option "uid=1001" or missing value
Failed to mount /media/sda.[/HTML]
when i do "sudo mount -a" i get
[HTML]mount: /etc/fstab: parse error at line 3 -- ignored[/HTML]
my fstab is:
[HTML]UUID=<my UUID num>  /media/ssd   ext4  uid=1001,rw,users  0   2[/HTML]
Any suggestion on how to fix this issue?
Thanks

---

### Post by #&amp;thj^% on 2022-03-19
You may want to include:
```
cat /etc/fstab
```

---

### Post by ravsmith82 on 2022-03-19
Thanks for your quick reply. 
i am really brand new to this with no prior experience in coding but where can i include this?
Thank you again for your help.

---

### Post by #&amp;thj^% on 2022-03-19
> **ravsmith82 said:**
> Thanks for your quick reply. 
i am really brand new to this with no prior experience in coding but where can i include this?
Thank you again for your help.
In your next reply, copy from the terminal, paste back in code tags to preserve the formatting.
see my signature for how to use code tags. Thanks

---

### Post by ravsmith82 on 2022-03-19
cat /etc/fstab :
```
LABEL=writable  /        ext4   defaults        0 1
LABEL=system-boot       /boot/firmware  vfat    defaults        0       1
UUID=d72347ac-3cc4-46fa-bad0-01fbe9d782bb       /media/flux     ext4    uid=1001                                                                   ,rw,users       o       2

```

---

### Post by #&amp;thj^% on 2022-03-19
Nice Thanks!
This needs correcting
```
UUID=d72347ac-3cc4-46fa-bad0-01fbe9d782bb       /media/flux     ext4    uid=1001                                                                   ,rw,users       o       2
```
To this:
```
UUID=d72347ac-3cc4-46fa-bad0-01fbe9d782bb       /media/flux     ext4          defaults        0       0 
```
Presuming you have the correct UUID, checked with:
```
sudo blkid
```

---

### Post by ravsmith82 on 2022-03-19
That fixed it, Thank you so much!!!

---

### Post by #&amp;thj^% on 2022-03-19
Good Job. :)

---

