---
title: "New accounts don't have home folders!"
date: 2006-11-06
forum: General Help
---

### Post by Aleksandersen on 2006-11-06
Hi,

When I create new accounts they don't get home folders.

How can I fix this!?

I use the "user and groups" application from an administrative account to create the new accounts.

---

### Post by kkinder on 2006-11-06
You're probably using useradd, not adduser. The former only manipulates the user list, while the latter creates home directories, etc.

Cheesy, yes.

---

### Post by bsussman on 2006-11-06
> **Aleksandersen said:**
> Hi,

When I create new accounts they don't get home folders.

How can I fix this!?

I use the "user and groups" application from an administrative account to create the new accounts.
If these new users login, what does the command 'pwd' (in a terminal) show?

---

### Post by Aleksandersen on 2006-11-07
> **kkinder said:**
> You're probably using useradd, not adduser.
How do I tell the difference in the GUI interface?

---

### Post by PriceChild on 2006-11-07
As far as i know... their directories will be created on the first log in.

---

### Post by bsussman on 2006-11-07
> **PriceChild said:**
> As far as i know... their directories will be created on the first log in.

Not in any version of linux, unix, bsd, minix or qutenix that I know of...

Please provide documentation references for your statement.

---

### Post by bsussman on 2006-11-07
> **Aleksandersen said:**
> How do I tell the difference in the GUI interface?
The gui interface should be doing the right thing.
Even the underlying config file has no setting to avoid making a home directory.
What is listed in the home directory column in the gui?  I cannot find a way to tell the gui not to create a home dir.

In a terminal, if you

```
cat /etc/passwd
```what directory is listed for the new users?  It is the 6th field (: is the separator).  

For instance:

```
bos@Dillon:~$ cat /etc/passwd|grep bos
bos:x:1000:1000:Brandon Sussman:/home/bos:/bin/bash
bos@Dillon:~$
```as you can see, bos's home dir is /home/bos

BTW, the x is where the password used to be, many, many years ago :).  It is now kept in a separate file, thus allowing us access, without root privs, to the vital info on how a user is configured.

---

