---
title: "Ubuntu 14.04 root folder full in one afternoon"
date: 2016-02-27
forum: General Help
---

### Post by nicole14 on 2016-02-27
I left my laptop on for a few hours and was surprised to find my battery flat because normally it lasts. I plugged it in and when I turned it in it had an internal error message and told me I'm out of disk space. 

Disk usage analyzer reveals that my root folder is at 100% usage of 263 GB. I must have been rather overly conservative when I made my root folder that huge! 

Running df -h reveals:
/dev/sda8 size:46GB used:44GB Avail:0 use:100% Mounted on /
With no other folders higher than 50%

Does anyone have any idea what could have happened? I thought I was starting to become an ok ubuntu user but this is completely beyond me. I don't understand much of what the other posts about full root folders are saying.

---

### Post by v3.xx on 2016-02-27
```
sudo find / -name '*' -size +1G
```

That give you any help?  The command will list files over 1G in size.

Also this may help

[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by nicole14 on 2016-02-27
Thanks! I'll take a look through that post it looks helpful.

In the mean time I managed to isolate my problem to log files using
sudo du -sh ./*
And entering the offending folder and repeating until I found huge log files. I got this idea from [http://askubuntu.com/questions/432836/how-can-i-check-disk-space-used-in-a-partition-using-the-terminal-in-ubuntu-12-0/432842](http://askubuntu.com/questions/432836/how-can-i-check-disk-space-used-in-a-partition-using-the-terminal-in-ubuntu-12-0/432842)

I found this command helpful 
ls -lSh
To produce a nicely arranged list of files from biggest to smallest in the current directory 

I deleted two 14 GB log files using
cat dev/null > file.log
As recommended in the last under-rated post here: [http://askubuntu.com/questions/515146/very-large-log-files-what-should-i-do](http://askubuntu.com/questions/515146/very-large-log-files-what-should-i-do)

I'm still not sure what caused the log files but I've saved the last few lines in case it happens again. For now I'm happy to continue working! 

Somehow whatever I did to those two 14GB log files reduced my root folder from over 200GB to 16.8GB according to the Disk usage analyzer? (After restarting)

---

### Post by grahammechanical on 2016-02-27
Root and other folders are variable in size. They have to be. As you have found out it is entirely possible for the root folder to increase in size as much as it is able to up to the limit of the size of the Ubuntu partition.

Regards.

---

