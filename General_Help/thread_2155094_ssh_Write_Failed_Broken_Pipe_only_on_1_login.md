---
title: "ssh Write Failed: Broken Pipe only on 1 login"
date: 2013-06-17
forum: General Help
---

### Post by chiques on 2013-06-17
Hello Community,
I can ssh into my admin account no problem. When I try to ssh into a shared account, i get the following error:

> Wire Failed: Broken pipe

```

user1@notebook:~$ ssh user1@10.2.4.1 -p 99
user1@10.2.4.1's password: 
Welcome to Ubuntu 12.04.2 LTS (GNU/Linux 3.5.0-34-generic i686)

 * Documentation:  https://help.ubuntu.com/

0 packages can be updated.
0 updates are security updates.

Last login: Sun Jun 16 00:12:35 2013 from notebook.home
user1@user1-mainlab:~$ exit
logout
Connection to 10.2.4.1 closed.

```

Fails here:
```
user1@notebook:~$ ssh user2@10.2.4.1 -p 99
user2@10.2.4.1's password: 
Write failed: Broken pipe
user1@notebook:~$ 

```


This was all working flawlessy until my ISP's internal hub locked up and had to reboot. This inturn caused my fiber router to freeze. My router had been assigned a new IP address.


I'm thinking it's something with the login permissions or apache settings.

Thanks for any help!

---

### Post by fj401971 on 2013-06-17
If you can ssh in with one user name, it's not the ISP or the router.  It's got to be on the computer you're trying to ssh into.

---

### Post by chiques on 2013-06-17
Is there a configuration file that is account specific that I can check?

---

### Post by fj401971 on 2013-06-17
check your /etc/ssh/sshd_config file   make sure you don't have any login restrictions under AllowUsers or AllowGroups or DenyGrouops or DenyUsers

---

### Post by fj401971 on 2013-06-17
If the username you are trying to login with is root, then there is also a PermitRootLogin setting as well

---

### Post by chiques on 2013-06-17
Ok, I'll check that out. Thanks

---

### Post by HiImTye on 2013-06-17
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
if you're using a proxy, make sure that it's configured to not proxy local traffic

---

### Post by chiques on 2013-06-20
> **fj401971 said:**
> check your /etc/ssh/sshd_config file   make sure you don't have any login restrictions under AllowUsers or AllowGroups or DenyGrouops or DenyUsers

I restored the sshd_config file back to its original. Now when I try to login the broken pipe error is no longer coming up.

**_New Problem:_**
When I try to log in as the user2, it immediately logs me out.

---

### Post by chiques on 2013-06-20
```

user1@notebook:~$ ssh user2@10.2.4.1 -p 99
user2@10.2.4.1's password: 
Welcome to Ubuntu 12.04.2 LTS (GNU/Linux 3.5.0-34-generic i686)

 * Documentation:  https://help.ubuntu.com/

0 packages can be updated.
0 updates are security updates.

Last login: Wed Jun 19 21:57:17 2013 from notebook.home
Connection to 10.2.4.1 closed.
user1@notebook:~$ 


```

This is my log:

> 
Jun 19 21:57:48 user1-remote-server sshd[4176]: Accepted password for user2 from notebook port 59130 ssh2
Jun 19 21:57:48 user1-remote-server sshd[4176]: pam_unix(sshd:session): session opened for user user2 by (uid=0)
Jun 19 21:57:48 user1-remote-server sshd[4293]: Received disconnect from notebook: 11: disconnected by user
Jun 19 21:57:48 user1-remote-server sshd[4176]: pam_unix(sshd:session): session closed for user user2


---

### Post by chiques on 2013-06-20
something is screwed up in the home directory of user2. There are a bunch of files missing e.g. /.ssh. Not sure what could have caused this. I created a new account and ssh works just fine with it. I was there was a way to restore all of these basic files in the home directory. I guess I'll just have to create a new account and transfer all of my stuff.

Thanks for everyone's help.

---

