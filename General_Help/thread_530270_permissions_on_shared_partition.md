---
title: "permissions on shared partition"
date: 2007-08-20
forum: General Help
---

### Post by creznedmick on 2007-08-20
Greetings
I am trying to share directories across a network between two fiesty machines.  The directories show up OK under the relevant computer under a windows (samba) network. When I try to open them I get a "The  conents of this directory could not be displayed" pop-up. A shared directory in my home folder shows and opens. I guess samba is working fine and its permissions are OK.

 "ls -l" shows owner as "root" and permissions as read write execute for owner, read execute for group and read only for others.  When I try to alter the permission of the mounted partitions "sudo chmod 0777  /media/hdc* "  there is no error message but a "ls -l" shows the permissions haven`t changed.
I guess I will have to change fstab, but am unsure of the best way to make it easy for myself as I am the only user of both computers. 
Anyone had experience of a similar situation
Michael

---

### Post by maldojr88 on 2007-08-20
homes....just try 
$sudo chmod 777 /media/hdc*

ommit the '0'

and remember if it is just a file that you want to change the permisions use 666 instead of 777

but i think ur clear that its a directory...also ....if that doesnt work try changing the owner

try 

$sudo chown **newOwner** **filenameORpath**

let me know how it goes

---

### Post by creznedmick on 2007-08-20
Greetings maldojr88
Thanks for the reply
The change to chmod made no difference and the chown told me I did not have permission, even though owner root has rwx permissions listed
Michael

---

### Post by creznedmick on 2007-08-20
Greetings
I edtied fstab and changed: default to user and umask to 000 and all is well.  Not much in the way of security but as I am the only user, I guess I`ll just have to trust myself
Thanks for the help
Michael

---

