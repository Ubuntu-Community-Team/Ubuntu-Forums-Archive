---
title: "user@computer missing from server and ssh prompt"
date: 2013-02-03
forum: General Help
---

### Post by cristofaro on 2013-02-03
I recently reinstalled Ubuntu Server 12.04.1 (amd64) on my server and then added a user account for myself ('user2') in addition to the default administrator one ('user1') that was setup during the install.

When I do both a local login and/or login via ssh I experience the folling issue (which in this case is a demonstration of ssh the login):

```
mediapc@anothercomputer:~$ ssh -l user1 192.168.1.2
user1@servercomputer:~$ 
```

```
mediapc@anothercomputer:~$ ssh -l user2 192.168.1.2
$ 
```

As you can see for the added user2 no 'user@computer:~' is displayed, simply the trailing '$'. I suspect the reason I am having this trouble is down to the method I used to add user2 to the system, in this case:

```
sudo useradd -d /home/user2 -m user2
sudo passwd user2
sudo groups user1
user1 : group1 group2
sudo adduser user2 group1
sudo adduser user2 group2
```

It would be great to know how I can fix this problem and have user2 login and display the following instead:```
user2@servercomputer:~$
```

Should be a pretty straightfoward fix, I tried searching but I guess I do't know the specific jargon to find help on this issue.

---

### Post by steeldriver on 2013-02-03
'useradd' will probably have created user2 with its login shell set to /bin/sh instead of /bin/bash - and /bin/sh is symlinked to the dash shell

You can check by looking at the entries in your /etc/passwd file

If you want to change the login shell to bash, you can use 'usermod'

```
sudo usermod -s /bin/bash user2 
```You might want to look at 'adduser' instead of 'useradd'

---

### Post by cristofaro on 2013-02-03
Thanks for the reply.

I have a look at the /etc/passwd file as you suggested and you're exactly right I noticed a couple differences between user1 and user2:

```
user1:x:1000:1000:NAME,,,:/home/user1:/bin/bash
user2:x:1001:1001::/home/user2:/bin/sh
```

In particular the reference to /bin/sh instead of /bin/bash. 

I'll have a good look at the differences between 'adduser' and 'useradd'.

Just as an aside is it bad practice (or would it even work) to directly edit /etc/passwd? I'll use the usermod command as suggested.



Edit: That command totally fixed my problem! Thanks again :)

---

