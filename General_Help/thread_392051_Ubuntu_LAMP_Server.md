---
title: "Ubuntu LAMP Server"
date: 2007-03-24
forum: General Help
---

### Post by dudds on 2007-03-24
Hi I just did an install of a Ubuntu LAMP server and was wondering what the default MySQL password is??


Thanks,
David

---

### Post by dudds on 2007-03-24
For anyone interested it seems the answer is to set the root password yourself via the following command

"sudo mysqladmin -u root password newrootsqlpassword"

---

### Post by pbrockway2 on 2007-03-24
As far as I know the root user does not have a password when mysql is first
installed - which is why it is recommended that you set one (eg with the
command you suggest) straight away.

---

### Post by jenhsun on 2007-03-24
In terminal, type:
sudo mysql_secure_installation

---

