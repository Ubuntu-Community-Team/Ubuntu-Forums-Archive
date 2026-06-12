---
title: "VMware Server won't install"
date: 2006-12-12
forum: General Help
---

### Post by Phototrek1 on 2006-12-12
Hello, I have downloaded everything needed for vmware server.  The problem is that when i try to insall it Vmware says there is another version.  I had Vmplayer installed.  But have since removed it.  

Here is the Guide (pdf) i'm following (I get stuck at top of page 3)
I have also adaped it. Instead of logining at vmadmin i log in as grant.
[http://www.tudra.net/wp/wp-content/uploads/2006/07/VMWare%20Server%20on%20Ubuntu%20Dapper%20Drake.pdf](http://www.tudra.net/wp/wp-content/uploads/2006/07/VMWare%20Server%20on%20Ubuntu%20Dapper%20Drake.pdf)

Here is where i get stuck! ](*,)  

> grant@grant-desktop:~$ sudo mkdir /home/vmware_machines
grant@grant-desktop:~$ sudo chown grant:grant /home/vmware_machines
grant@grant-desktop:~$ sudo tar -xzf VMware-server-1.0.0-28343.tar.gz -C /home/grant
grant@grant-desktop:~$ sudo tar -xzf VMware-mui-1.0.1-29996.tar.gz -C /home/grant
grant@grant-desktop:~$ cd /home/grant/vmware-server-distrib
grant@grant-desktop:~/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

grant@grant-desktop:~/vmware-server-distrib$


Is there any way to remove what ever is being detected.  Thanks

---

### Post by yabbadabbadont on 2006-12-12
Remove the /etc/vmware directory and all its contents if it exists.

---

### Post by Phototrek1 on 2006-12-12
Thanks, It works like a charm.  :)

---

