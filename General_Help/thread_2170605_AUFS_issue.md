---
title: "AUFS issue"
date: 2013-08-26
forum: General Help
---

### Post by demslam on 2013-08-26
Howdy All. I have a question in regards to AUFS i currently have Ubuntu Server 12.04 running on my server. The server has 6 drive installed in it, i am pooling 4 drive (boot drive is not in the pool).

Below is my /etc/fstab 
```
# / was on /dev/sdc1 during installation
UUID=888d044b-50b4-47f6-acdb-b41449588fc2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=63787265-ae5d-4ba7-abaf-bfb88743b7e4 none            swap    sw              0       0

UUID=1ecea5e5-27a1-4d0b-be9b-e4ad61fbcc8a       /mnt/int01      ext4    defaults        0       2
UUID=316de53a-6967-4198-a273-40e192e73d05       /mnt/int02      ext4    defaults        0       2
UUID=97cb9b49-530c-4696-8761-88c301c1c155       /mnt/int03      ext4    defaults        0       2
UUID=fee95544-be95-4faa-968e-112a89897a8c       /mnt/int04      ext4    defaults        0       2
#(Snapraid Parity)
UUID=d0f351f2-d00d-4d2a-be5f-f69715d6d0e5       /mnt/int05      ext4    defaults        0       2
```

Below is my /etc/rc.local
```
mount -t aufs -o br:/mnt/int01=rw:/mnt/int02=rw:/mnt/int03=rw:/mnt/int04=rw,sum,create=mfs,udba=reval none /storage
```

The issue i am having is i am unable to access the majority of the files as a regular user. I can see the information as root (sudo), i have tried "sudo chmod -R 755 /storage/" but that did not fix the issue. If i go to individual drives /mnt/int0# information is there and is accessible as a user. 

Thanks for any help.

---

### Post by demslam on 2013-08-30
I was able to get around the issues by change/modifying ownership through direct mount and not through AUFS mount.
ie ```
chmod 777 -R /storage/
``` didnt work but ```
chmod 777 -R /mnt/int0*
``` did.

---

