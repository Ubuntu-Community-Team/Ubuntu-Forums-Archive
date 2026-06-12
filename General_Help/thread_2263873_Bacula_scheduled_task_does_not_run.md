---
title: "Bacula scheduled task does not run"
date: 2015-02-04
forum: General Help
---

### Post by vangend.robert on 2015-02-04
I have successfully set up Bacula on Ubuntu 12.04 server to run some  back / restore jobs. However, this is only from the console program.  Whenever the scheduled job runs, there are errors. Primarily permission  issues.  
 
When I run the console program, I am root. However, the directory that I  am backing up too has full rights for user = bacula. Also user bacula  owns these directories. 
 
Right now I am backing up to hard disk, I will eventually change the bacula configuration to backup to DELL LT02. However, the permissions on the actual backup file are confusing to me. I have not created a group "tape" yet the file that has been created belongs to group "tape". I am not sure if bacula's setup process created this group or not. I am not sure if this is the cause of the problem.

-rwxrwx--- 1 bacula tape 1124084641 Jan 31 21:22 pool1-0001

I hope this explanation is detailed enough. 
 
If anyone has some suggestions / feedback, I would much appreciate it.

---

### Post by Habitual on 2015-02-04
Seen [https://help.ubuntu.com/community/Bacula](https://help.ubuntu.com/community/Bacula) ?

---

