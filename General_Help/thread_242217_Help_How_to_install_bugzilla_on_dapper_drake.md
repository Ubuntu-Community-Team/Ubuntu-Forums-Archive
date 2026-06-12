---
title: "Help: How to install bugzilla on dapper drake ?"
date: 2006-08-23
forum: General Help
---

### Post by intel on 2006-08-23
How do i install bugzilla on dapper drake 6.06 ?

If tried through synaptic & failed it gives a vague error message & fails

just try installing it i am sure the same thing will happen to you
(i.e this problem is consistent & repeatable)

thanks

intel

---

### Post by greenosity on 2006-08-30
I have also been trying to install Bugzilla and was getting errors. I looked at the Terminal after it failed and there were errors about the user debian-sys-maint accessing MySQL. This seems to be a common problem with various things; not just the Bugzilla package. I fixed the install errors by copying the password in the file /etc/mysql/debian.cnf and then resetting the password for the debian-sys-maint user in MySQL:

mysql> SET PASSWORD FOR 'debian-sys-maint'@'localhost' = PASSWORD('blah');

where blah is the password from the file debian.cnf.

Why these passwords don't match to begin with confuses me - I'm a newbie to Linux.

Now, Bugzilla seems to be installed but I get errors trying to access it. I try http://localhost/bugzilla and get some error about 'cgi-bin'. "You must be looking for index.cgi" (or something like that).

Can anyone help out on where to go from here?  :-k

---

