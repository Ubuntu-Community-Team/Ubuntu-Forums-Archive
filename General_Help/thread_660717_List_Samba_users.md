---
title: "List Samba users"
date: 2008-01-07
forum: General Help
---

### Post by jmvidalvia on 2008-01-07
It seems to be a simple question, but I could't find help anywhere.:(
How to know all Samba users?
There's must be a way to keep up to date your Samba users database..
Thanks!

---

### Post by danwood76 on 2008-01-07
It depends how youve inserted the different users.

If you have all the users loded into /etc/samba/smbusers then you can simply do
```

cat /etc/samba/smbusers

```

That will list all the users assuming you are using the standard user mapping method.

How have you added the users to your samba server?

regards,
Danny

---

### Post by jmvidalvia on 2008-01-07
Thanks!
But I am afraid I don't have this file.
I add users by:
```
#smbpasswd -a newuser
```
:(
Thanks again.

---

### Post by danwood76 on 2008-01-07
they may also be stored in /etc/samba/smbpasswd
I dont have my samba setup like this so I cant test, but to list do:

```

cat /etc/samba/smbpasswd
```

regards,
Danny

---

### Post by jmvidalvia on 2008-01-07
I insist I don't have this file.
From my Edgy laptop:
```
jm@jm:/etc/samba$ ls -la
total 80
drwxr-xr-x   2 root root  4096 2007-12-27 10:52 .
drwxr-xr-x 123 root root  8192 2008-01-07 12:31 ..
-rw-r--r--   1 root dhcp    54 2008-01-07 12:31 dhcp.conf
-rw-r--r--   1 root root     8 2006-07-11 15:27 gdbcommands
-rw-r--r--   1 root root 12730 2007-12-27 10:52 smb.conf
-rw-r--r--   1 root root 10606 2007-03-25 13:07 smb.conf.230307
-rw-r--r--   1 root root 12345 2007-03-26 10:46 smb.conf.260307
-rw-r--r--   1 root root 12624 2007-03-27 11:35 smb.conf.270307
jm@jm:/etc/samba$ 

```

From my debian server:
```
debian:/etc/samba# ls -la
total 40
drwxr-xr-x  2 root root  4096 2007-11-16 12:17 .
drwxr-xr-x 66 root root  4096 2007-12-27 12:15 ..
-rw-r--r--  1 root root    38 2007-09-10 13:34 dhcp.conf
-rw-r--r--  1 root root     8 2007-05-30 11:53 gdbcommands
-rw-r--r--  1 root root 11474 2007-11-16 11:58 smb.conf
-rw-r--r--  1 root root 10690 2007-09-10 13:58 smb.conf.100907
debian:/etc/samba# 
```

I installed Samba from official repositories and use standard commands to configure everything.
:confused:

There's a similar threat [here]("http://ubuntuforums.org/showthread.php?t=23616"): I posted a new one as it was already quite old, and gave no solution.
This issue looks very strange: ¿didn't anyone try to manage and update Samba users  in Linux systems?
Thanks.

---

### Post by a2brute on 2008-01-14
Well, I too really need to find a list of samba users, but after checking 3 threads on this very same issue, It is clear that with Ubuntu the samba user files and a few other configuration files are not stored in the "standard" locations.  (according to samba.org)  So the question becomes, has anyone ever actually found where the user and account information is stored when samba is installed via the Ubuntu package manager?  All the other threads end without a solution being found.  :confused:

I now know the meaning of embarrassment when I (the sysadmin) tells the CTO I know how to view and edit samba user info, and then I jump on the ubuntu server and have to admit to him that I cannot find or print a list as promised.  :(

If anyone else has found this information, then lets get the file locations posted here so this does not happen to another open source admin. :)

Thanks.

---

### Post by harrysales on 2008-02-14
If i've lost things I cd to root(/) and issue the command find | grep 'lost thing'.
for your issue I did find | grep smb and found /usr/bin/smbpasswd which is the executable. Bollox!!!

---

### Post by jmvidalvia on 2008-02-14
> **harrysales said:**
> If i've lost things I cd to root(/) and issue the command find | grep 'lost thing'.
for your issue I did find | grep smb and found /usr/bin/smbpasswd which is the executable. Bollox!!!

Thanks!
But I am afraid this won't help: I know where executables are, and in fact I use this executable to do: #smbpasswd -a 'user'
The problem **is where users are stored**, or, h**ow to list users**.
Thanks again.

---

### Post by jmvidalvia on 2008-02-15
Got it!
The first point to check is your smb.conf, authentication chapter.
If you have
passdb backend = smbpasswd
then your users are in:
/etc/samba/smbpasswd

But in case (as mine) you have:
passdb backend = tdbsam
then you must use:

```
# pdbedit -Lw
```

You should read [this]("http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/passdb.html")
Good luck!

---

