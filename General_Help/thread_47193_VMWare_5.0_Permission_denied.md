---
title: "VMWare 5.0 Permission denied"
date: 2005-07-07
forum: General Help
---

### Post by ioan629 on 2005-07-07
Hi,

can't start vmware as normal user, getting permission denied on /usr/bin/vmware. All VMWare related files like /usr/bin/vm* or /usr/lib/vmware/* are root only. I tried to change permissions manually and finally managed to start vmware gui as normal user but it doesnt work to start guest system. If I start VMWare as root it runs without any error messages. 

Somebody has an idea how to fix this problem? ](*,) 
Thanks in advance

Ivan

---

### Post by pointym5 on 2005-07-07
[QUOTE=ioan629]Hi,

can't start vmware as normal user, getting permission denied on /usr/bin/vmware. All VMWare related files like /usr/bin/vm* or /usr/lib/vmware/* are root only. I tried to change permissions manually and finally managed to start vmware gui as normal user but it doesnt work to start guest system. If I start VMWare as root it runs without any error messages. 

Somebody has an idea how to fix this problem? ](*,) 
Thanks in advance

Ivan[/QUOTE]

What are the permissions on the directory where the guest system files are stored? Those need to be such that your non-root user can read and write.

---

### Post by ioan629 on 2005-07-08
~/vmware und ~/.vmware dirs with guest system have proper permission, the problem is other. The problem ist that vmware installer doesnt set proper permissions for vmware bin and vmware lib dirs by default, so I cant start vmware without modifying permissions.


have you set the permissions manually after vmware install? can you look in your installation what permissions and ownership you have for /usr/bin/vm* and /usr/lib/vmware/*


Thanks

---

### Post by pointym5 on 2005-07-08
All the permissions look fine to me (555 mostly) on my system.

---

### Post by ioan629 on 2005-07-08
Finally I solved this problem in putting permissions manually to 555 and vmware-vmx to +s. Now its working!

Thanks for help!

---

### Post by linuxcity on 2005-09-10
[QUOTE=ioan629]Finally I solved this problem in putting permissions manually to 555 and vmware-vmx to +s. Now its working!

Thanks for help![/QUOTE]
 I'm new to Linux. Could you please explain the steps into solving this problem?
thanks,
Linux Newbie

---

