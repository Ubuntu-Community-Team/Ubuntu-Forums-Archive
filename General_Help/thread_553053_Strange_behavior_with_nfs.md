---
title: "Strange behavior with nfs"
date: 2007-09-17
forum: General Help
---

### Post by jmvidalvia on 2007-09-17
What I do in my laptop:
```
jm@jm:~$mount ubuntu:/home/datos /home/jm/nfs
jm@jm:~$ cd nfs
jm@jm:~/nfs$ ls -l
total 36
drwxrws---  7 nobody administracion 4096 2007-09-06 11:32 administracion
drwxrws---  5 nobody compras        4096 2007-01-08 12:07 compras
drwxrws---  6 nobody direccion      4096 2007-09-14 16:00 direccion
drwxrws--- 22 nobody direccion      4096 2007-07-27 12:37 finanzas
drwxrws--- 10 nobody compras        4096 2007-09-07 13:56 import
jm@jm:~/nfs$ id
uid=1000(jm) gid=114(admin) grupos=4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),29(audio),30(dip),46(plugdev),100(users),112(scanner),114(admin),115(fuse),1001(desa),1002(administracion),1003(direccion),1004(compras)
jm@jm:~/nfs$ cd compras
bash: cd: compras: Permiso denegado
jm@jm:~/nfs$ 

```
I can not access to compras/ although user jm belongs to that group (gid 1004).

In Ubuntu server:
```

jmd@ubuntu:~$ id jm
uid=1030(jm) gid=1001(desa) grupos=1001(desa),1002(administracion),1003(direccion),1004(compras)
jmd@ubuntu:~$ 

ubuntu:/# cat /etc/exports
/home/datos 192.168.103.0/255.255.255.0(rw,no_root_squash,async,subtree_check)

```

I forced gid > 1000 to be the same in both machines.
User "jm" is registered in ubuntu server as well as in my laptop and belongs to all groups > 1000.

The mistery is: ¿why can I acces all /home/datos folders except /home/datos/compras, although I belong to "compras" group in both machines?

Thanks in advanced!

---

