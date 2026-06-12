---
title: "user #1000 locks permissions"
date: 2020-08-26
forum: General Help
---

### Post by Gnusboy on 2020-08-26
Hi all, It's been a while

I keep running into a problem when trying to change permissions on a folder/file.

I was trying to move a folder to an external HDD but the folder would not allow the transfer. I checked the permissions
and it shows "Basic, Permissions, and local network share
The permission showed owner as "user #1000" and "group" as 1000 (no hash in front)
I think "User 1000" is supposed to be the first user registered on the system. AS I am the administrator, I am supposed to 
have all privileges to the entire folder. Is this accurate? But at the bottom of the notice it says, " 
"you are not the owner so you cannot change these permissions"
If I could get to the administrator privileges, I can fix the problem - at least for this particular folder. But the "user accounts" is not letting
change anything either.
I have had the same issue many times. Sometimes I can access the user accounts to change the permissions that way.
But the "user #1000" stops any action.
Any ideas on how to fix this?
Thanks.

---

### Post by Impavidus on 2020-08-27
UserID 1000 is the first user, the one created during installation. But it shouldn't say user 1000, but give username instead, so it may be missing from the passwd file. Was user 1000 deleted after creating a new admin user?

Show this:```
grep "$USER\|1000" /etc/passwd
stat /path/to/misbehaving/file
groups
```(Feel free to hide personal details like your real name.)

---

### Post by Gnusboy on 2020-08-27
I guess user #1000 would have been created when I upgraded to 16.04, but that was many years ago and I don't remember.

I assume I was supposed to enter the commands line by line. Here's the output:

grep "$USER\|1000" /etc/passwd
ubuntu:x:999:999:Live session user,,,:/home/ubuntu:/bin/bash
ubuntu@ubuntu:~$ stat /path/to/misbehaving/file
stat: cannot stat '/path/to/misbehaving/file': No such file or directory
ubuntu@ubuntu:~$ groups
ubuntu adm cdrom sudo dip plugdev lpadmin sambashare
ubuntu@ubuntu:~$

---

### Post by grahammechanical on 2020-08-27
Are you trying to use a Ubuntu live session to move that file? The replies you got from those 3 commands show that you are running a live session.

In Ubuntu even if our username has administrator privileges we always work as a standard user unless we prefix terminal commands with the word "sudo" and then enter our password. And then our authority will last as long as we are entering commands and the authority will expire a few minutes after we stop entering commands. And we revert to a standard user again.

If you are working from an installed version of Ubuntu and are using the file manager to move a file that another user has created then the file manager in the latest versions of Ubuntu should prompt  for a password. As the administrator the password word you used to log in to Ubuntu is the password that is needed.

You may know all this but it is not clear from your posts that you do know these things.

Regards

---

### Post by Impavidus on 2020-08-28
Where I wrote /path/to/misbehaving/file I expected you would substitute the path to the misbehaving file.

---

