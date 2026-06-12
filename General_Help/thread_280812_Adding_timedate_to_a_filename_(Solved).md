---
title: "Adding time/date to a filename (Solved)"
date: 2006-10-20
forum: General Help
---

### Post by Aulden on 2006-10-20
Hey all, 

Can someone tell me how or if it's possible to add the date to a filename automatically? 

For example I have a backup program to run daily and I want it to save the file as 'Backup03102006'... that is 'Backup' with the date proceeding. This will mean backups wont overwrite each other and I can keep track of them without manually renaming and so on. 

How do I do that?

I think in Windows it would be Backup%g%G for the date then time... 

Any ideas? 
Is it the same?

Thanks for any help...

---

### Post by aysiu on 2006-10-20
This doesn't directly answer your question, but you might be interested in [rdiff-backup](http://ubuntuforums.org/showthread.php?p=1217737#post1217737), which does incremental backups and would save a lot of space over separate backups by date.

---

### Post by Aulden on 2006-10-20
Thanks a heap. I'll look into that.

I'm having to backup many computers over a network so will have to check if it has the ability to fetch files over a network. 

When I started I got tired of looking for a program that did everything I needed so I put a script together myself that seems to be working ok. Only this filename thing could be good help. 

The reason is that our projects team want archives available for each day of the last week plus a weekly backup. 

Thanks again... I'll be sure to check it out!!!

---

### Post by aysiu on 2006-10-20
According to [its website](http://www.nongnu.org/rdiff-backup/): > rdiff-backup backs up one directory to another, **possibly over a network**. The target directory ends up a copy of the source directory, but extra reverse diffs are stored in a special subdirectory of that target directory, so you can still recover files lost some time ago. The idea is to combine the best features of a mirror and an incremental backup. rdiff-backup also preserves subdirectories, hard links, dev files, permissions, uid/gid ownership, modification times, extended attributes, acls, and resource forks. Also, rdiff-backup can operate in a bandwidth efficient manner over a pipe, like rsync. Thus you can use rdiff-backup and ssh to securely back a hard drive up to a remote location, and only the differences will be transmitted. Finally, rdiff-backup is easy to use and settings have sensical defaults.

---

### Post by yota on 2006-10-20
Hi,

in linux it should be filename-$(date +%F-%T)
> 
yota@linbook:~$ touch filename-$(date +%F-%T)
yota@linbook:~$ ll file*
-rw-r--r-- 1 yota yota 0 2006-10-20 09:30 filename-2006-10-20-09:30:28


note that the syntax $(...) applies to any command, and means "use the output of the included command as a string".
To see details about 'date' command and +%F-%T meaning look at 'man date'.
(by the way %F is full date and %T is full time)

Please note that this works in the terminal or in bash scripts, but not in nautilus.

Hope this helps!

---

### Post by Aulden on 2006-10-20
That's exactly what I was looking for. 

Excellent.

Thanks a heap!!!

And thanks to aysiu. Had a look and that program looks helpful too. 

Excellent!

---

