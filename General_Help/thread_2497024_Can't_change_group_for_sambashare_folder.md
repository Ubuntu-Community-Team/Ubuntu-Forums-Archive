---
title: "Can't change group for sambashare folder"
date: 2024-04-20
forum: General Help
---

### Post by linusthecat on 2024-04-20
Hi, rather inexperienced GNU/Linux user looking to set up an external USB drive to be a sambashare folder. The drive is mounted to the directory ```
/usbshare
```

When I use ```
sudo chgrp sambashare /usbshare
``` I get the following error: ```
chgrp: changing group of '/usbshare': Operation not permitted
```

I've tried several solutions I've found from searching but nothing seems to be solving my issue.

My configuration for ```
smb.conf
``` is as follows:

```
[NAS]

     path = /usbshare
     guest ok = Yes
     writeable=Yes
     read only = No
     force group = sambashare
     create mask=0777
     directory mask=0777
     force user = server
```

Thanks in advance for any help.


EDIT: 

This is solved. I discovered that permission was being denied because the disk was not partitioned to be a Linux filesystem. I followed the directions here: [https://linuxconfig.org/how-to-format-disk-in-linux](https://linuxconfig.org/how-to-format-disk-in-linux) and now the chgrp command went through successfully.

---

### Post by TheFu on 2024-04-22
Please use the "Thread Tools" Button near the top of the page and mark this thread "SOLVED" so you don't waste people's time. Thanks.

---

