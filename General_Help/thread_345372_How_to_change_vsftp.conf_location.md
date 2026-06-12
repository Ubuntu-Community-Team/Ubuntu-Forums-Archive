---
title: "How to change vsftp.conf location ?"
date: 2007-01-24
forum: General Help
---

### Post by slo on 2007-01-24
In ubuntu 6.10:
#apt-get install vsftpd
then vsftpd.conf is in /eat/vsftpd.conf
I want to change the vsftpd.conf to /etc/vsftpd/vsftpd.conf
What file should  I to modufy for vsftpd start normal ?

---

### Post by renzokuken on 2007-01-24
you could always make a soft link to /eat/vsftpd.conf in /etc/vsftpd

---

### Post by slo on 2007-01-25
My means is :
if you apt-get install proftpd
then you can find /etc/default/proftpd file and change proftpd service config file location
but when I apt-get install vsftpd
there isn't vsftpd in /etc/default/ ,  I just change the vsftpd conf file location to /etc/vsftpd/vsftpd.conf

---

### Post by taurus on 2007-01-25
```
sudo ln -s /etc/vsftpd/vsftpd.conf /etc/vsftpd.conf
```

---

