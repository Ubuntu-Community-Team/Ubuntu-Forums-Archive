---
title: "User password ldm"
date: 2021-01-06
forum: General Help
---

### Post by Freiklite on 2021-01-06
Hi,
I created a user with the following commands:
```
 sudo adduser --force-badname  Zety
  
```
and I checked with:
```
 ~$ cat /etc/passwd
********
Zety:x:1001:1001:,,,:/home/Zety:/bin/bash


```

When I run with ldm (light display manager) the password is considered to be wrong.
I read some posts but I didn't find any solution.

Thank you very much your future assist,
Bye.

---

### Post by ajgreeny on 2021-01-06
Does the option **--force-badname** allow upper case in usernames?

From man adduser.conf it appears that you need to add some other option.
```
NAME_REGEX_SYSTEM
              Names of system users are checked against this regular expression.  If --system  is  supplied  and  the
              name doesn't match this regexp, user creation in adduser is refused unless --force-badname is set. With
              --force-badname set, only weak checks are performed. The default is as for the default  NAME_REGEX  but
              also allowing uppercase letters.
```

---

### Post by #&amp;thj^% on 2021-01-06
Remove the capital "Z" adding user "zety" as ajgreeny points out.
Also then if you want to add the user to the sudo group run the following command.
```

sudo adduser <username> sudo
```

---

### Post by Freiklite on 2021-01-06
Hi,
Thanks for the answers.

I deleted "Zety":
```
sudo userdel -r Zety


```
I created "zety" as user:
```
sudo adduser zety


```
I checked for the presence of "zety":
```
$ cat /etc/passwd | grep zety
zety:x:1001:1001:,,,:/home/zety:/bin/bash


```
When I logged in the system displayed: "incorrect password"

Bye.

---

### Post by #&amp;thj^% on 2021-01-06
I had no issues with:
```
sudo adduser --gecos '' zesty
sudo: unable to resolve host me.ubuntu.com: Name or service not known
[sudo] password for me: 
Adding user `zesty' ...
Adding new group `zesty' (1003) ...
Adding new user `zesty' (1001) with group `zesty' ...
Creating home directory `/home/zesty' ...
Copying files from `/etc/skel' ...
New password: 
Retype new password: 
passwd: password updated successfully
```
And do you see a difference in mine:
```
zesty:x:[COLOR="#FF0000"]1001:1003[/COLOR]:,,,:/home/:/bin/bash
```

---

### Post by Freiklite on 2021-01-06
Hi,
I typed:
```
~$ sudo su
 then 
passwd zety


```
I typed a new password for "zety".
Everything works well.

Thank you very much for your help.
Happy new year.


P.S.:
~$ cat /etc/passwd | grep zety
zety:1001:1001:,,,:/home/zety:/bin/bash
~

---

### Post by #&amp;thj^% on 2021-01-06
just goes to show, there's more than one way to skin a cat. ;)
Glad it's working now.
Kind regards

---

