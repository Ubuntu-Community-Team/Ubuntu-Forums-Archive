---
title: "make a filesystem only mounted by root...."
date: 2017-12-15
forum: General Help
---

### Post by rizler132 on 2017-12-15
Hello everyone,

I have a user foo.. which is in group users. it is also in another group wheel.
wheel has sudo permissions.but inorder to execute sudo wheel has to enter root password. 
I have 5 disks in my system. all of them are asking user password while mounting them by clicking nemo sidebar disks icon/name...
I want some of them to ask root password to mount using nemo sidebar clicking....
I tried using fstab put the nouser option in that disk options but no use. it is still asking only the `foo` password.
How can I make sure that it is only mounted by root.... using fstab or udisksctl rules.....

---

