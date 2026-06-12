---
title: "freshclam.log locked by another process???"
date: 2017-06-07
forum: General Help
---

### Post by xenon3 on 2017-06-07
I just rebooted, so there can be no other process then through my internet connection, must be from outside, I mean outside my computer

```


p@p-MH35:~$ sudo freshclam
[sudo] password for p: 
ERROR: /var/log/clamav/freshclam.log is locked by another process
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).
p@p-MH35:~$ sudo freshclam
ERROR: /var/log/clamav/freshclam.log is locked by another process
ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).
p@p-MH35:~$ 


```

---

### Post by SeijiSensei on 2017-06-07
It could be locked by a freshclam process.  Try running
```
sudo lsof | grep freshclam
```
You'll get back one or more entries with the process number that is using the file.  If you want, you can kill the process with "sudo kill -9 pid" where "pid" is the process number.

---

### Post by xenon3 on 2017-06-07
Thanks! This KILL command worked. I am running LUBUNTU by the way, maybe LUBUNTU has "freshclam" running in the background (always)

---

### Post by vasa1 on 2017-06-07
Lubuntu doesn't come with freshclam installed by default.

---

### Post by howefield on 2017-06-07
> **xenon3 said:**
> Thanks! This KILL command worked. I am running LUBUNTU by the way, maybe LUBUNTU has "freshclam" running in the background (always)

ClamAV will update itself automatically so chances are that it was in the process of updating itself it when you ran the freshclam command.

In any case, to update manually you have to stop the running daemon first.

---

### Post by SeijiSensei on 2017-06-07
The freshclam daemon is installed by default as part of the clamav-freshclam package and runs automatically when the machine boots.  In the future, I'd avoid interfering in this process and just let it manage itself.

---

