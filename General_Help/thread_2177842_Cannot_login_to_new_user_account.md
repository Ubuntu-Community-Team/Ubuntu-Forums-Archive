---
title: "Cannot login to new user account"
date: 2013-09-30
forum: General Help
---

### Post by mogdad on 2013-09-30
Hi,
I have just created a new user account ("test") using the User Accounts gui but cannot login to it - it just kicks me back to the login screen over and over again. /home/test has been created and the files in it look ok. I'm using 12.04 LTS 64 bit last updated a day or two ago. I can still login to my existing admin account as normal

$ ls -al /home/test/
total 32
drwxr-xr-x  3 test  test  4096 Sep 30 20:27 .
drwx------  6 mogdad mogdad 4096 Sep 30 20:29 ..
-rw-r--r--  1 test  test   220 Sep 30 19:02 .bash_logout
-rw-r--r--  1 test  test  3486 Sep 30 19:02 .bashrc
-rw-r--r--  1 test  test  8445 Sep 30 19:02 examples.desktop
-rw-r--r-- 1 test  test   675 Sep 30 20:29 .profile



Looking at previous similar posts, there can be problems with file ownership but everything looks ok and I've done 'chown -R test:test /home/test' to be sure. 

I have also made another new account using adduser but i get the same problem.

Can't see anything weird in /etc/passwd either: test:x:1001:1001:Test,,,:/home/test:/bin/bash

Grateful for any suggestions!
thanks

---

### Post by steeldriver on 2013-09-30
Your whole /home directory (i.e. the **parent **of your new user's home directory) is owned by someone else and not readable / executable - it needs to be owned by root and have r-x permissions for 'group' and 'other'

```
drwxr-xr-x 6 root root 4096 Aug  8 12:28 /home
```


> **mogdad said:**
> Hi,
I have just created a new user account ("test") using the User Accounts gui but cannot login to it - it just kicks me back to the login screen over and over again. /home/test has been created and the files in it look ok. I'm using 12.04 LTS 64 bit last updated a day or two ago. I can still login to my existing admin account as normal

$ ls -al /home/test/
total 32
drwxr-xr-x  3 test  test  4096 Sep 30 20:27 .
[COLOR=#ff0000]**drwx------  6 mogdad mogdad 4096 Sep 30 20:29 ..**[/COLOR]
-rw-r--r--  1 test  test   220 Sep 30 19:02 .bash_logout
-rw-r--r--  1 test  test  3486 Sep 30 19:02 .bashrc
-rw-r--r--  1 test  test  8445 Sep 30 19:02 examples.desktop
-rw-r--r-- 1 test  test   675 Sep 30 20:29 .profile



Looking at previous similar posts, there can be problems with file ownership but [COLOR=#ff0000]**everything looks ok**[/COLOR] and I've done 'chown -R test:test /home/test' to be sure. 

I have also made another new account using adduser but i get the same problem.

Can't see anything weird in /etc/passwd either: test:x:1001:1001:Test,,,:/home/test:/bin/bash

Grateful for any suggestions!
thanks

---

### Post by mogdad on 2013-10-07
That has fixed it  - thanks!
I moved /home to a separate hdd a while ago and obviously didn't get the permissions right - but didn't notice anything wrong until now as I was the owner of /home.

---

