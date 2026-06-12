---
title: "Phpmyadmin on 22.04"
date: 2022-08-21
forum: General Help
---

### Post by cearlp2 on 2022-08-21
Searching for how to set a password for root in phpmyadmin shows a way using the User Accounts tab from the main page.
However, I installed phpmyadmin (version 5.1.1deb5ubuntu1) on 22.04 and do not find a User Accounts tab.
Could the version installed be a subset of the full version and have no User Accounts tab?

---

### Post by TheFu on 2022-08-22
> **cearlp2 said:**
> Searching for how to set a password for root in phpmyadmin shows a way using the User Accounts tab from the main page.
However, I installed phpmyadmin (version 5.1.1deb5ubuntu1) on 22.04 and do not find a User Accounts tab.
Could the version installed be a subset of the full version and have no User Accounts tab?

Tools like this should only be accessible from the localhost, never from any remote systems directly.  That forces login validation and using something like ssh-tunnels even to connect to the system first, drastically improving security.  Setup ssh-keys and it becomes very secure, since no end-users should be allowed on any system running a DBMS.

The same rule applies to any admin tool or remote desktops (RDP/VNC) which have really poor security.

[https://security.stackexchange.com/questions/146281/how-to-operate-phpmyadmin-with-an-ssh-tunnel](https://security.stackexchange.com/questions/146281/how-to-operate-phpmyadmin-with-an-ssh-tunnel) has the ssh tunnel command.

---

### Post by cearlp2 on 2022-08-22
I am trying this on localhost. There is no User Accounts tab on the main page.
I wa signed on as the administrator of phpmyadmin.

---

### Post by cearlp2 on 2022-08-24
Question answered!!! I found out that setting a root user password using mysql alter user statement and then using root when logging in to phpmyadmin, a User Accounts tab is there. Using another login, even though it had all privileges, no User accounts tab was displayed.

---

### Post by TheFu on 2022-08-24
a) thanks for sharing the solution.
b) Please help the wider community by using the "Thread Tools" button and marking this thread SOLVED - this helps everyone else.

---

