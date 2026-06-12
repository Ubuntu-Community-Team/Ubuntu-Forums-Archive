---
title: "mysql access denied no matter what i do"
date: 2007-09-20
forum: General Help
---

### Post by tefflox on 2007-09-20
I've been searching for three hours to solve this problem, finding hundreds of solutions that elude me.

error:

```
#28000Access denied for user 'root'@'localhost' (using password: NO)
```

among others.  I don't know what to do.  I am exhausted.

---

### Post by cabinboy on 2007-09-20
Did this happen after a fresh mysql installation? Or did you have a working mysql before?
If your mysql just broke recently, what was your last operation before it broke?
Does the problem still remain after restarting the system?

The more information you provide, the sooner you'll get an answer.

---

### Post by tefflox on 2007-09-20
> **cabinboy said:**
> Did this happen after a fresh mysql installation? Or did you have a working mysql before?
If your mysql just broke recently, what was your last operation before it broke?
Does the problem still remain after restarting the system?

The more information you provide, the sooner you'll get an answer.

Before and after.  I have solved this problem twice before.  Last week all I had to do was ```
sudo touch /var/run/mysqld/mysqld.sock
```and add the adapter to the config.yml file.  

I installed mysql-server last night.  Now no solutions work.  I thought I had that installed already, but my system is touchy of late, after reconfiguring X.  Everything is touchy, as you can imagine.

Now I will restart the system.  See if that helps.

---

### Post by tefflox on 2007-09-20
Problem solved.  Now it works like butter.  :popcorn:

---

