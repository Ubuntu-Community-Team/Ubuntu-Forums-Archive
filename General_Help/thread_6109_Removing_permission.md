---
title: "Removing permission"
date: 2004-11-24
forum: General Help
---

### Post by jozmak on 2004-11-24
Hi
I am new to ubuntu. I just mounted a partition what i intend to use as storage space but the system keeps telling me that i have no permission to do anything on that partition. There is a lock on it and i cannot remove it and as a result i  cannot save or open a file on the partition. Can anyone tell me how to  remove this restriction. This is the line from the fstab file. I tried to include every possible options i could think of in the line but no avail.

/dev/hdb3 /mnt/hardDrive ext3 user,exec,dev,suid,auto 0 0

In fact i want to remove these permission restrictions from all files as default because this is a home computer and i don't need this super security.

Before, i had some experience with fedora. There you could log in as root, which let you do graphically everything. This was very convenient. In ubuntu there is no way to login as root, as far as i know, and do things graphically. Is there a workaround this? Because doing everything from the command line is to time consuming and often cumbersome.

Thanks
jozmak

---

### Post by zenwhen on 2004-11-24
I use the following for my ext3 drive, which I read from and write to as a user. 

/dev/hdb3        /mnt/storage     ext3    defaults         1   2

---

### Post by jozmak on 2004-11-24
Thanks.
I tried your entry, but still permission denied.
This drives me crazy.

---

