---
title: "running sshd on 2 ports?"
date: 2005-08-12
forum: General Help
---

### Post by nbx909 on 2005-08-12
how do i get sshd to run on port 22 and port 433 at the same time? my school blocks port 22 and i want to be able to adminster my server from school.

---

### Post by heimo on 2005-08-12
man sshd_config knows:
 >    Port    Specifies the port number that sshd listens on.  The default is
             22.  Multiple options of this type are permitted.  See also
             ListenAddress.
 

So: I'd try to add another Port line to /etc/ssh/sshd_config and restart ssh 
```
sudo /etc/init.d/ssh restart
```

---

### Post by nbx909 on 2005-08-12
i tried but i can't figure out how to seprate them i've tried 22,433 and 22 433 and 22;433. But it just errors. So how do i seperate them?

---

### Post by mird on 2005-08-12
Just add another line... e.g. ```
Port 22
Port 433
```

---

### Post by nbx909 on 2005-08-12
thank you!

---

