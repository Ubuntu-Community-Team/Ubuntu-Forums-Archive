---
title: "Unable to Resove Host"
date: 2017-01-20
forum: General Help
---

### Post by curticegough on 2017-01-20
Hi.  When I use **sudo su** to get into root,  It gives me this.

```
curtice@linuxloverpc:~$ sudo su
sudo: unable to resolve host linuxloverpc
[sudo] password for curtice: 
root@linuxloverpc:/home/curtice#
```

What does this mean?:confused:  All of the sudo commands still work.  It just says unable to resolve host when I use sudo.

---

### Post by SeijiSensei on 2017-01-20
Look in the file /etc/hosts.  Is there an entry for linuxloverpc?  By default Ubuntu associates the hostname with the IP 127.0.1.1
```
127.0.1.1      linuxloverpc
```
If that line isn't in /etc/hosts, add it by editing the file with the command
```
sudo nano /etc/hosts
```
Use Ctrl-X plus "Y" to save the file and exit when you're done.

If that line exists, but with another hostname instead, you can either replace the entry with the one above, or add "linuxloverpc" after the hostname in the file.  The first name in an /etc/hosts entry is the "canonical" hostname, but you can add others that are aliases for that name.

---

### Post by curticegough on 2017-01-20
Thanks!  That worked great!  I love the Ubuntu Forums because you always get an answer within an hour.

---

