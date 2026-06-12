---
title: "SSH trerminal on Apache server"
date: 2020-02-09
forum: General Help
---

### Post by cearlp on 2020-02-09
How does one determine if Apache installed on ubuntu 18.04 LTS has ssh terminal access?

---

### Post by Holger_Gehrke on 2020-02-09
What exactly do you mean by that question ?

Apache (httpd) is one piece of server software, sshd is a different one. You can install it from the package openssh-server. If it is already installed then 'systemctl status ssh' should tell you whether or not it's up and running.

Holger

---

### Post by cearlp2 on 2020-02-09
Thanks, that answers my question.

---

