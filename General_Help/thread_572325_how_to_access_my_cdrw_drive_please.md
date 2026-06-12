---
title: "how to access my cdrw drive please"
date: 2007-10-10
forum: General Help
---

### Post by redarrow01 on 2007-10-10
advance thank you.

i am new at this please help me..

i have made a new directory called www i now want to add apache to the directory www
from my cd drive how do i do that please.

i tried but it wrong so upset so hard all this......

but i wont give up.....

this is wrong but i tried

 sudo mount /computer/cd rom 1

then how do i copy all them files to the www folder

---

### Post by redarrow01 on 2007-10-10
i tried this 

$ cd /media/cdrom

then this

$ sudo cp -R www/*

i get the error

cp: missing destination file operand after `www/*'
Try `cp --help' for more information.

please help thank you.

---

### Post by PmDematagoda on 2007-10-10
Did you try:-

```
sudo mount /dev/cdrom1 /media/cdrom1
```

---

### Post by redarrow01 on 2007-10-10
i tried that mate dosent work but thank you.


this works it get the termanl change to cdrom...
$ cd /media/cdrom

but this dosent copy the files to www directory

$ sudo cp -R www/*

---

### Post by PmDematagoda on 2007-10-10
Are you trying to copy the files to the CD?

---

### Post by redarrow01 on 2007-10-10
i am trying to get all the files from the cd to a diretory of www mate.

thank you for your time.


have i got this backwards mate.

please help....

---

### Post by PmDematagoda on 2007-10-10
I believe you are missing the path to where the files are supposed to be copied.

---

### Post by redarrow01 on 2007-10-10
i am currently in the media root ok.

drwxr-xr-x  4 root         root 4096 2007-10-10 15:18 .
drwxr-xr-x 22 root         root 4096 2007-10-10 15:04 ..
lrwxrwxrwx  1 root         root    6 2007-10-09 18:23 cdrom -> cdrom0
drwxr-xr-x  2 root         root 4096 2007-10-09 18:23 cdrom0
-rw-r--r--  1 root         root   82 2007-10-10 15:18 .hal-mtab
-r-Sr-----  1 root         root    0 2007-04-15 13:03 .hal-mtab-lock
dr-xr-xr-x  1 myname root 2048 2007-10-10 15:12 server aps

now i need to goto the server aps

so i do this 

cd /media/server aps

i get told that the directory dosent exist, but it there 

anyone please....

---

### Post by redarrow01 on 2007-10-10
ok everyone what this mean please.
mount: special device /dev/hdb does not exist

but i must tell ya when the cd in the drive the cd disk works also can see the disk information please help cheers.

---

