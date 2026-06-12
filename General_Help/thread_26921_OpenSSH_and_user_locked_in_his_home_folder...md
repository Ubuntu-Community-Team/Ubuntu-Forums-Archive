---
title: "OpenSSH and user locked in his home folder.."
date: 2005-04-14
forum: General Help
---

### Post by CrustyDOD on 2005-04-14
What the title says..
Currently if i log in with gftp client i can go outside my home folder and browse my whole disk..

How can i lock every user into his home folder: /home/_user_ ?

All i want for users to have access to my ssh server over sftp clients..
I guess this has something to do with shells /shell/bash <-- current one.
I would like for users to have something like: /shell/ftponly..

---

### Post by dataw0lf on 2005-04-14
The best way to do so is to use a form of chroot. This[guide](http://www.tjw.org/chroot-login-HOWTO/) should be enough to get you started.

---

### Post by CrustyDOD on 2005-04-14
not working for me..

did exactly the same like in that guide, tried to login with gftp, result: loggs in but freezes at password, no more action from than on..

then i tried again with other user and same happens..

oh well..

---

### Post by crazybill on 2005-04-14
Your solution is easy.

Install vsftpd as your FTP server:

apt-get install vsftpd

Then configure your file gedit /etc/vsftpd.conf
The configuration file is easy to set up. It defaults with one anonymous folder /home/ftp as read only. You need uncomment the ability for users to log in, allow writing privildeges, and keeping users to thier own folder. You simply remove a few "#".

Make sure you restart with /etc/init.d/vsftpd restart  after making your changes

Crazy Bill

---

