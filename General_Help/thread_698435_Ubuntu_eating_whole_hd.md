---
title: "Ubuntu eating whole hd"
date: 2008-02-16
forum: General Help
---

### Post by bbarnaby on 2008-02-16
Gutsy is telling me I have no room left on a 500gb hard drive, even though I have nowhere near that amount of media. I went and deleted a lot of files to make more room this morning, and within an hour or so I'm again getting a warning that I am out of space. I have no files coming in. The only thing I can think to do is backup my home directory to my external HD and reinstall. Seems kinda drastic, though. Any ideas would be appreciated! Thanks.

---

### Post by chrisccoulson on 2008-02-16
Have you emptied the trash? What is the output of 
```
df -h
```

---

### Post by bbarnaby on 2008-02-16
Yes, trash is empty. I couldn't log in this a.m., I had to open a terminal and delete a bunch of stuff by hand to log in. Once I did, I got rid of even more stuff, so plenty of room. 45 mins later, warning msg: /dev/sda1 out of room. That was about 22 gb in less than an hour. No files coming in. I'm stumped.

---

### Post by chrisccoulson on 2008-02-16
Can you still post the output of df -h, so I have a bit of a better idea of what your setup looks like. You havent posted enough information for anybody to be able to help

---

### Post by LO Matt on 2008-02-16
You probably have a log file that is out of control.  check the contents of /var/log

---

### Post by patrickfromspain on 2008-02-16
I also think you're having a problem with some log files that's growing more and more...

---

