---
title: "Permissions problems with multiple distros"
date: 2007-08-05
forum: General Help
---

### Post by davem2312 on 2007-08-05
Hey all,

I have 3 distributions installed, and obviously run into problems because my uid is different.  I would like to make a separate data partition, and mount to /home/<user> or /home/<user>/data  or something. To do this smoothly, I need to do one of a few things.

1. I could change ownership of data partition every time I boot up a different distro

2. I could mount the partition in a certain uid and gid (I know this is possible with fat32, but not sure with ext3)

3. I could "add" an owner to the files in the partition, but again, I don't know if this is possible, I believe chown just changes the ownership.

Could anyone provide some help for me?  Thanks

--Dave

---

