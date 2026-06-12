---
title: "Update error"
date: 2008-01-02
forum: General Help
---

### Post by macmichael01 on 2008-01-02
Hello I am getting this ubuntu update error on my VM and I am not sure why it is:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo2_1.4.10-1ubuntu4.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo2_1.4.10-1ubuntu4.2_i386.deb)
  404 Not Found [IP: 91.189.88.37 80]

And I am connected to the internet.

---

### Post by icheyne on 2008-01-02
I can access that update server, using the ping command on that IP address (ping 91.189.88.37), so the server itself works. It could be a temporary problem.

---

### Post by Seisen on 2008-01-02
Try updating you source list because and then see if it works because when I click on that link it says not found and the versions also dont' match either.

[[URL="http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/"]http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/]("http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo2_1.4.10-1ubuntu4_i386.deb")
[/URL]
[http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo2_1.4.10-1ubuntu4.2_i386.deb]("http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo2_1.4.10-1ubuntu4.2_i386.deb")

---

### Post by macmichael01 on 2008-01-02
that was simple enough updating sources worked. thanks Seisen

---

