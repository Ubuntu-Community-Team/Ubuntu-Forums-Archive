---
title: "Open directory as another user?"
date: 2015-07-19
forum: General Help
---

### Post by peter1897 on 2015-07-19
I am trying to enter the mysql folder /var/lib/mysql using the mysql user name but it doesn't work. I tried these commands:

```
max@ubuntu:~$ sudo cd -u mysql /var/lib/mysql/
max@ubuntu:~$ sudo -u mysql cd /var/lib/mysql/
```
but i get:
```
sudo: cd: command not found
```

The mysql folder is owned by user mysql:
```
drwx------ 7 mysql     mysql    4096 2015-07-19 00:01 mysql
```


Why it doesn't work?

---

### Post by dino99 on 2015-07-19
cd  /var/lib/mysql/

---

### Post by peter1897 on 2015-07-19
This doesn't work because i am not the owner of the directory and permissions are set only for the user mysql which is the owner:
```
max@ubuntu:~$ cd /var/lib/mysql/
bash: cd: /var/lib/mysql/: Permission denied
```

---

### Post by Lars Noodén on 2015-07-19
What do you want to do with or in the other directory?

---

### Post by peter1897 on 2015-07-19
I just want to enter the mysql directory without the need to switch to root user every time i have to do it.

---

### Post by Lars Noodén on 2015-07-19
But then what do you want to do?

If you want to look at the files that are there, you can change group membership of the directory.  What happens after that depends on the permissions there.

```

chgrp peter1897 /var/lib/mysql/
chmod g+rx /var/lib/mysql/

```

That will allow you to look at the directory.  If you want to do that for more than one user, then you'll have to choose a different group.

---

### Post by peter1897 on 2015-07-19
I am just wondering if it is possible to enter the directory as another user without changing permissions or do anything else and only using the command: **sudo -u run_as_user**

---

### Post by Lars Noodén on 2015-07-19
Yes it is, but using cd would not give you any other permissions, such as those needed to see which files are there.  You could "sudo ls" or something instead.  cd is too ephemeral.

---

### Post by peter1897 on 2015-07-19
I guess, then, what i am trying to do is not possible.

---

### Post by Lars Noodén on 2015-07-19
Not with cd at least, that's why I was asking about the goals.  With cd the best you can do is change your working directory to a directory in which you have no other permissions.  Separate programs, like ls, are needed to read the file names and so on, so they are what the sudo utility should be pointed at instead of cd.  cd isn't like a gate that you go through and then can do whatever, the directory's permissions (or lack thereof) still apply even if you change the working directory.

---

### Post by Morbius1 on 2015-07-19
> morbius@mub14:~$ sudo -u tester1 cd /etc/samba
[sudo] password for morbius: 
sudo: cd: command not found

You might try this instead:
> morbius@mub14:~$ su tester1
Password: [COLOR=#0000cd]<--- asking for tester1's password not morbius'[/COLOR]
[COLOR=#0000cd]tester1[/COLOR]@mub14:/home/morbius$ cd /etc/samba [COLOR=#0000cd]<--- morbius has become tester1 for this session[/COLOR]
[COLOR=#0000cd]tester1[/COLOR]@mub14:[COLOR=#0000cd]/etc/samba[/COLOR]$ su morbius
Password: 
morbius@mub14:/etc/samba$


---

