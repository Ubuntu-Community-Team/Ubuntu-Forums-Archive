---
title: "xinetd restriction problem"
date: 2015-05-12
forum: General Help
---

### Post by anon9815 on 2015-05-12
i have configured xinetd not to allow access to sshd to systems on the local network however it continues to allow access my /etc/xinetd.d/ssh is as follows   ```
 service ssh {         socket_type = stream         protocol = tcp         port = 3200         wait = no         user = root         server = /usr/sbin/sshd         server_args = -i         no_access = 192.168.0.1/24         disable = no } 
```  no sure why its all on one line

---

### Post by ian-weisser on 2015-05-13
Are you married to an xinetd solution?
I shifted all my xinetd tasks to Upstart years ago. And thence to systemd recently.

---

### Post by anon9815 on 2015-05-13
if possible i would like to use xinetd for this

---

### Post by Lars Noodén on 2015-05-13
Would that work with 192.168.0.0/24  instead?

---

### Post by anon9815 on 2015-05-13
turns out that i should have disabled ssh.service and that's what was causing the problem

---

