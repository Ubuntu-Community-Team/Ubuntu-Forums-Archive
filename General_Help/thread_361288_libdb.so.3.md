---
title: "libdb.so.3"
date: 2007-02-14
forum: General Help
---

### Post by ubufrog on 2007-02-14
Hi

I am having problems running vmware-mui on ubuntu 6.10 64-bit. When i try to run /usr/lib/vmware-mui/apache/bin/httpd.vmware i get the error:

error while loading shared libraries: libdb.so.3: cannot open shared object file: No such file or directory

I know the file is there, i can see it in /usr/lib/vmware-mui/lib and the config file /etc/vmware-mui/locations even states its looking for the file in /usr/lib/vmware-mui/lib/libdb.so.3.

So i really am out of ideas right now, anyone know how to fix this?

Thanks in advance

---

### Post by enderox on 2007-03-12
stuck here with the same issue.

did you sort this out ?

---

### Post by ubufrog on 2007-03-12
Nope, never got a decent reply (even from VMTN), let me know if u find anything I spent about a week trying to find an answer.

---

### Post by enderox on 2007-03-13
I've installed libdb2 although the vmware mui still doesn't want to start

edit:
manually running the httpd.vmware command pointed me towards further issues with libssl.so.X and libcrypto.X which both existed in the ....../vmware/lib directory but not /lib which seemed to be where it was looking for it (even if it shouldn't have been), so I copied them across (but I should change them to symlinks).
I also found references (in these forums) to /bin/sh symlinked to dash rather than bash also causing issues. I fixed that too.

I've now got the MUI working. Further playing necessary, I can't login as root to unlock full MUI functionality.

---

### Post by clacroix on 2007-03-30
> I also found references (in these forums) to /bin/sh symlinked to dash rather than bash also causing issues. I fixed that too.

This has worked for me, I have changed the symlink of */bin/sh* to point to *bash* for the time of vmware-mui installation and then chenged it back. Nothing else was needed [Ubuntu DT 6.10]

Thanks for the hint enderox ... ;-)

---

### Post by shoulder on 2007-04-17
Please refer to [[SIZE="6"]this site[/SIZE]]("http://users.piuha.net/martti/comp/ubuntu/server.html") 

Martti Kuparinen had support the solution and instructions to install vmware server on ubuntu dapper / edge.

---

### Post by Lu3ke on 2008-05-13
Ok, I went to Martti's site, but he doesn't mention the libdb.so.3 error at all... this is where I am stuck, since httpd will not start.

(the full error is: "error while loading shared libraries: libdb.so.3: cannot open shared object file: No such file or directory")

Any ideas?

   - Luke

---

