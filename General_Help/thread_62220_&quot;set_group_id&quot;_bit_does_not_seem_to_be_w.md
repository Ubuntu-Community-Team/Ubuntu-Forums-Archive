---
title: "&quot;set group id&quot; bit does not seem to be working"
date: 2005-09-03
forum: General Help
---

### Post by gokusandwich on 2005-09-03
hi. i'm trying to use the "set group id" bit, and am having some trouble.
i read from this site:
[http://docsrv.caldera.com:507/en/man/html.C/chmod.C.html](http://docsrv.caldera.com:507/en/man/html.C/chmod.C.html)
the following, about the "set group id" bit:
Sets owner or group ID on execution of the file to that of the owner of the file. The mode ``u+s'' sets the user ID bit for the file. The mode ``g+s'' sets the group ID bit. Other combinations have no effect. When the group ID bit is set on a directory, all files created under it subsequently receive the group ID of that directory. When the group ID bit is not set, files are created with the group ID of the creating process/user.

i have a directory, called "submitted", for which i've set the "set group id" bit. if i do an "ls -l", i can see that the bit has been set:
drwxrwsr-x 354 chris easyweaze 26496 2005-08-31 08:59 submitted

now, i have a daemon running (mldonkey/mlnet) which downloads files to this directory. it runs under my user account, chris.

so, from what i understand, any files created under this "submitted" directory should be given a group id of "easyweaze", since easyweaze is the group set for "submitted".

however, when new files are downloaded to this directory, by mldonkey, they are owned by "chris", and have a group of "chris", as well:
-rw-r--r-- 1 chris chris 99323665 2005-08-31 08:58 filename.rar

creating files/directories on the command line or through text editors produces the expected results: the files have a group of easyweaze.
what am i doing wrong?

furthermore, i would like to have the files be "group writable", by default, as well, so that an application running with a group of "easyweaze" can write to the files. any thoughts on this would also be appreciated.

thanks in advance!
chris

---

### Post by plb on 2005-09-03
I believe this is because all files are being set as the daemons primary group chris _not_ the directory group though I could be wrong, as far as writable permissions check out the umask command I believe this is what your looking for but I'm a bit rusty on it but a little googling should help you out, I'm to tired to do it  :)

---

