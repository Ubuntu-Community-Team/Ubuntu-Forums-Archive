---
title: "Hard disk almost full"
date: 2007-01-26
forum: General Help
---

### Post by hallco on 2007-01-26
I have Edgy installed on a 66GB hard disk - 66239199
With "df" I am told that the disk is 98% full -i.e. 61284852, almost 63GB appears to be used.
When runing "du" this reports that my total files used add to 18664579 - i.e. 18GB
Where are the missing files filling up my disk?

---

### Post by taurus on 2007-01-26
```
df -h
```
When you ran du, where were you?  If you ran du while you are in your $HOME directory, then it only gave you the total space for /home/username, not the whole system.

```
cd /
sudo du
```

---

### Post by novice_geek on 2007-01-26
Hello,
 
I am having a similar problem myself.  I just recently added a second hard drive.  When I df (I actually perfer to use df -h), I see hda, which is 15.8GB total, with 12 used.  That's okay.  The new drive, hdb, is a 250GB SINGLE IDE drive.  It showed up as having about 13GB used right after I installed and formatted it.  I am using Edgy 6.10 LAMP on this machine, which was upgraded from Dapper LAMP.
 
Thanks, and good luck to hallco :)
 
Thanks,
Novice_Geek
 
btw, I am doing this in /, not in $HOME.  Also, I typically put type "df -h /" when I do it.

---

### Post by dcstar on 2007-01-26
> **hallco said:**
> I have Edgy installed on a 66GB hard disk - 66239199
With "df" I am told that the disk is 98% full -i.e. 61284852, almost 63GB appears to be used.
When runing "du" this reports that my total files used add to 18664579 - i.e. 18GB
Where are the missing files filling up my disk?

Various filesystems reserve space for root only, you are seeing a report of space available for non-root users (and processes).

If you want more information do a web search, there are many articles answering in detail the exact same question you have asked.

---

### Post by hallco on 2007-01-27
Thanks. I have discovered the problem to be unrestricted backups!

---

### Post by novice_geek on 2007-01-27
Hallco,
 
Could you please tell me how you found out about the unrestricted backups, and how you fixed your problem.  I am a Linux n00b, and so I am curious to find out and to see if that's why I have a similar problem on my system's disks.
 
Thanks,
Novice_Geek

---

### Post by trace_on on 2007-02-27
I'm also curious about what you say about the unrestricted backups. I am having the same problem with my hard disk and it's driving me insane. How did you fix it?
Cheers,
-Alex

---

