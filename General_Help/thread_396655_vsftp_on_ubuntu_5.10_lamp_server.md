---
title: "vsftp on ubuntu 5.10 lamp server"
date: 2007-03-29
forum: General Help
---

### Post by psykro on 2007-03-29
I have performed my first LAMP testing server installation using ubuntu 5.10 by following [this]("http://www.mysql-apache-php.com/") tutorial.

I have got everything working the way I want it, but I am stuck on one thing. I want to figure out how to set the system to set ftp uploaded files (using the ftp server vsftp) to have 755 permissions.

At the moment I have to upload the files and then set the permissions myself. How would I go about having that set by default when I file is uploaded?

(Thanks in advance)

---

### Post by psykro on 2007-03-29
Sorry I tend to do this, but I figured out the problem. 

I needed to uncomment local_umask=022 in vsftpd config.

---

