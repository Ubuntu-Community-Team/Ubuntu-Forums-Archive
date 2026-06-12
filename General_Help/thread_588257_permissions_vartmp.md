---
title: "permissions /var/tmp"
date: 2007-10-23
forum: General Help
---

### Post by jeepGuy on 2007-10-23
Greetings!

Background - we are setting up Ubuntu Server 7.10 to host a multi-user commercial application. Users will connect to the server with ssh, login with their individual username/password, and start the text-based application.

Trouble - the application stores its license management file in /var/tmp. When a regular user runs the application, the application cannot update the license file. When root runs the application, all is well.

We tried changing permissions on /var/tmp/mgmt.file and /var/tmp. We changed ownership of the directory and file, too. We also tried changing the group ownership to users, making sure our user is in group users. We still can't even list the directory.

```
john@heritage:~$ ls /var/tmp
ls: /var/tmp: Permission denied
```

We are out of ideas, and because the application is commercial software, we don't have the option of moving the license file out of /var/tmp. Thanks for any ideas.

---

### Post by seldenthuis on 2007-10-23
These are the permissions and ownership /var/tmp should have:
```

sudo chown root:root /var/tmp
sudo chmod 1777 /var/tmp

```

If that doesn't work, could you post the output of 'ls -dl /var/tmp' and 'ls -l /var/tmp', running as root?

---

### Post by mahousaru on 2007-10-23
What is stored in tmp?  

Could you 

```
ls -l /var/tmp
```

and also show the rights on the tmp directory itself.

**Don't follow the below until all hope is lost, as it is just a maybe option**

If u need to then you can use more advance file rights, you can enable it with

sudo apt-get install acl

which gives you access to 

getfacl and setfacl

This allows for multiple users and groups.  Also you can set file access to a much finer degree.

Been ages since I've read up on this, but if you need to I can try to revive my beer sodden brain cells :p

Personally I don't think you should need it.

---

### Post by pelle.k on 2007-10-23
[edit]*sorry, i didn't read that carefully enough. Don't mind anything i wrote :)* [/edit]

---

### Post by jeepGuy on 2007-10-23
Thanks, guys. Here are the results

```
root@heritage:~# ls -dl /var/tmp
drwxrwxrwt 2 root root 4096 2007-10-23 09:34 /var/tmp

root@heritage:~# ls -al /var/tmp
total 12
drwxrwxrwt  2 root root  4096 2007-10-23 09:34 .
drw-rw-rw- 14 root root  4096 2007-10-22 16:38 ..
-rw-r--r--  1 root root     0 2007-10-22 16:38 0904095902
-rw-rw-rw-  1 root root 1938 2007-10-22 16:38 .389885.dfr

root@heritage:~$ ls -dl /tmp
drwxrwxrwt 3 root root 4096 2007-10-22 16:43 /tm
```

Here is the error that the user gets

```
john@heritage:~$ flex
Cannot Open User Count .DFR File. << STATUS 28692 >>

john@heritage:~$ ls /var/tmp
ls: /var/tmp: Permission denied
```

---

### Post by seldenthuis on 2007-10-23
> drw-rw-rw- 14 root root  4096 2007-10-22 16:38 ..

It looks like you don't have the execute permissions set on /var.  To cd into a directory (or show it's contents with ls), the execute permissions need to be set.  This should fix it:
```
sudo chmod a+x /var
```

I'm not sure what else you need to do in /var, but it might be a good idea to remove the write permissions for everybody but root.

---

### Post by mahousaru on 2007-10-23
I wonder if the app is trying to delete the .dfr file as the t on the end of the directory rights wont allow that.  It is the sticky bit and on a directory it means that only the owners can delete the file.

Wait I just notice something else far more fundamentally wrong.  Your user is unable to ls -l /var/tmp

Have you ran anything to harden the rights of the box?  As a user should be able to ls that directory.

*EDIT*
Hee hee didn't spot the .. rights :)

---

### Post by jeepGuy on 2007-10-23
Added execute permissions on /var and all is good! Thanks, guys.

```
john@heritage:~$ ls -ld /var
drwxrwxrwx 14 root root 4096 2007-10-22 16:38 /var

john@heritage:~$ ls -al /var/tmp
total 12
drwxrwxrwt  2 root root 4096 2007-10-23 09:34 .
drwxrwxrwx 14 root root 4096 2007-10-22 16:38 ..
-rw-r--r--  1 root root    0 2007-10-22 16:38 0904095902
-rw-rw-rw-  1 root root 1938 2007-10-22 16:38 .389885.dfr
```

---

### Post by mahousaru on 2007-10-23
I'd like to highlight what seldenthuis said about the write rights on var.  Its a really bad idea! The defaults of 

drwxr-xr-x 15 root root

Should be fine for var especially in a multiuser server

---

### Post by jeepGuy on 2007-10-23
Thanks for taking the time to follow up and highlighting the write permissions on var. I changed permissions to

drwxr-xr-x 14 root root 4096 2007-10-22 16:38 /var

as seldenthuis and mahousaru recommended. Everything continues to work, and /var is safer.

---

