---
title: "Access to a ubuntu subdirectory from windows"
date: 2006-10-16
forum: General Help
---

### Post by madelman on 2006-10-16
Does anybody know if it is possible to access a subdirectory in ubuntu from windows?

For example I have a end-user, who does not know "anything". Giving her steps to use FTP to transfer files is like giving her to build a rocket so I need something simple and I thought to give her direct access to a subdirectory in ubuntu from windows, so she will be looking this server as another shared windows directory. 

Is that possible?

---

### Post by Kateikyoushi on 2006-10-16
If it is an ext partition you can mount it in windows. [Here is the Driver]("http://www.fs-driver.org/")
Total commander has reiserfs plugin and saw somwhere a free server which lets you mount xfs as well but could not manage to make it work.

---

### Post by madelman on 2006-10-16
Thank you. But this link you pointed talks about having windows and linux installed on the same machine. What I need is a windows client accessing an ubuntu server on different machines. 

I am not sure if Samba is the solution I need I just found some threads that talk about same issue I want to resolve. 

Thank you anyway.

---

### Post by mistab1034 on 2006-10-16
I think that samba is exactly what your looking for.

[http://ubuntuguide.org]("http://ubuntuguide.org") has a good howto on setting up a samba server.

---

### Post by BLTicklemonster on 2006-10-16
Excellent. I have been wondering how to do that.

---

