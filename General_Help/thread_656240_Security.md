---
title: "Security"
date: 2008-01-02
forum: General Help
---

### Post by jbm715 on 2008-01-02
I have a question relating to security which I have not been able to find an answer to elsewhere.  So say I want to  mount my Windows partition, I have to enter my password to do so.  However once I enter my password for one partition I can mount any other partition without having to enter my password.  I'm wanting to know if it is possible to change some settings around so that Ubuntu does not remember my password whenever I am mounting a partition or installing software.

Thanks,
-Jimbo

---

### Post by rubicon on 2008-01-02
Read more in sudo documentation (man sudo). You can alter the default time for shell to remember your administrative password (15 mins) in /etc/sudoers.

---

### Post by jken146 on 2008-01-02
The procedure for changing the sudo timeout is as follows.

Open a terminal and type
```
sudo visudo
```

Then find the line that begins with the word "Defaults" and add this to the end of that line: ```
,timestamp_timeout=2
```
This would set the timeout to 2 minutes.  Change it to 0 to be asked for your password every time you use sudo or to a negative number to never be asked.

---

### Post by jbm715 on 2008-01-02
Thanks jken146 and rubicon! I appreciate your quick responses.

---

### Post by ~LoKe on 2008-01-02
The sudo grace period seems like a considerably vulnerability to me...

---

