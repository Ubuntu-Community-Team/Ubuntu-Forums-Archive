---
title: "Accessing Directories ETC"
date: 2013-05-10
forum: General Help
---

### Post by elliotbeken on 2013-05-10
Hi All,

I have a Ubuntu server with a few users, how to i stop users who are not in the sudoes file from looking in certain home directories. I basic terms:

I would like to stop all other users from looking into my home dir... (i am the only sudo user on the server)

Thanks

---

### Post by scbingham on 2013-05-10
Default directory permissions should not allow users to access other users' home directories.

---

### Post by elliotbeken on 2013-05-10
I know they cant copy edit ETC but they can see the file names/folder names. I would like to stop this, see below example:

if not sudo user issues "cd /home/elliot/Photos" they can do "ls -a" and see contents....

---

### Post by steeldriver on 2013-05-10
You can change the mode of your home dir e.g.

```

user@host:~$ ls /home/steeldriver/
Desktop  Documents  Downloads  examples.desktop  Music  Pictures  Public  Templates  Videos
user@host:~$ 
user@host:~$ **sudo chmod 750 /home/steeldriver**
user@host:~$ 
user@host:~$ ls /home/steeldriver/
ls: cannot open directory /home/steeldriver/: Permission denied
user@host:~$ 

```

---

### Post by elliotbeken on 2013-05-10
Thanks this has done the trick !!!

---

