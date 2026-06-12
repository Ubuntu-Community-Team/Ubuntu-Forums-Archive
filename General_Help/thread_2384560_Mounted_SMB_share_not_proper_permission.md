---
title: "Mounted SMB share not proper permission"
date: 2018-02-08
forum: General Help
---

### Post by u5tabil2 on 2018-02-08
I have manage to mount a SMB share that is password protected into Ubuntu. And I am able to read and see all folders of that share. But I am unable to write/delete stuff. I have tried searching but not sure what the problem really is or how to solve it.

Anyone know how I can have it set with proper permission?

I have edited the fstab with this:

```
#Samba FreeNAS share
//1.1.1.10/Media        /FreeNAS/Media  cifs    rw,username=xxx,password=xxx,uid=1001,gid=1001        0       0
//1.1.10/NAS            /FreeNAS/NAS    cifs    rw,username=xxx,password=xxx,uid=1001,gid=1001        0       0

```
I have then used the sudo mount -a. But still same problem.

Please help.

---

### Post by Morbius1 on 2018-02-08
And what happens when you do this:

//1.1.1.10/Media        /FreeNAS/Media  cifs    rw,username=xxx,password=xxx,uid=1001,gid=1001[COLOR=#0000cd]**,nounix**[/COLOR]        0       0
//1.1.10/NAS            /FreeNAS/NAS    cifs    rw,username=xxx,password=xxx,uid=1001,gid=1001[COLOR=#0000cd]**,nounix**[/COLOR]        0       0

---

### Post by u5tabil2 on 2018-02-09
seems problem was me being tired. uid=1001 was wrong set this to user you want. then group id the same.

---

