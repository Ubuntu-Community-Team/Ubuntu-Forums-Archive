---
title: "Ghost users (gone - no logout in /var/run/utmp)"
date: 2007-11-18
forum: General Help
---

### Post by Ferdl on 2007-11-18
Hello everybody. I've been using Ubuntu for sometime, but this is my first post here. My "problem" is that  in /var/run /utm there're ghost records, like:
```
fsanz    tty2                          Fri Nov 16 18:25    gone - no logout
```

It's not a real problem, but not knowing what's going on there is frustrating.  For example, right now I'm connected from work by ssh to my home box, and my girlfriend has a X session opened there -I bet for playing Caesar III with Cedega :) -, that i configured for running on  tty5 insteed tty6. So, what are those weird sessions in tty1 and tty2?


```
fsanz@fuckup: ~ $ w
 21:48:03 up 20 days, 14:57,  4 users,  load average: 1,72, 1,59, 1,45
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
martina  tty5     :0               Fri21    3:10   2:55   0.03s sh /home/martina/.xsession
fsanz    pts/1    193.219.103.42   19:37    0.00s  0.70s  0.01s w
fsanz@fuckup: ~ $ who
martina  tty5         2007-11-16 21:35 (:0)
fsanz    pts/1        2007-11-18 19:37 (193.219.103.42)
fsanz@fuckup: ~ $ last -f /var/run/utmp
fsanz    pts/1        193.219.103.42   Sun Nov 18 19:37   still logged in   
fsanz    tty2                          Fri Nov 16 18:25    gone - no logout 
martina  tty5         :0               Fri Nov 16 21:35   still logged in   
root     tty1                          Fri Nov 16 21:34    gone - no logout 

utmp begins Fri Nov 16 21:34:35 2007
fsanz@fuckup: ~ $ last -f /var/log/wtmp
fsanz    pts/1        193.219.103.42   Sun Nov 18 19:37   still logged in   
fsanz    pts/0        193.219.103.42   Sun Nov 18 18:16 - 21:25  (03:08)    
martina  pts/1        :0.0             Sun Nov 18 17:12 - 17:22  (00:09)    
martina  pts/0        :0.0             Sun Nov 18 17:12 - 17:19  (00:07)    
fsanz    pts/1        193.219.103.42   Sun Nov 18 02:54 - 07:19  (04:25)    
fsanz    pts/0        193.219.103.42   Sat Nov 17 20:12 - 07:19  (11:06)    
fsanz    pts/0        193.219.103.42   Fri Nov 16 23:07 - 07:06  (07:58)    
martina  tty5         :0               Fri Nov 16 21:35   still logged in   
root     tty1                          Fri Nov 16 21:34 - 21:34  (00:00)    
root     tty1                          Fri Nov 16 21:34 - 21:34  (00:00)    
fsanz    tty5         :0               Fri Nov 16 18:26 - 21:34  (03:08)    
fsanz    tty2                          Fri Nov 16 18:25 - 18:25  (00:00)    
fsanz    tty2                          Fri Nov 16 18:25 - 18:25  (00:00)    
root     tty1                          Fri Nov 16 18:25 - 18:25  (00:00)    
root     tty1                          Fri Nov 16 18:25 - 18:25  (00:00)    
martina  tty5         :0               Fri Nov 16 11:37 - 18:24  (06:47)    
root     tty1                          Fri Nov 16 08:44 - 08:44  (00:00)    
root     tty1                          Fri Nov 16 08:44 - 08:44  (00:00)    
root     tty1                          Fri Nov 16 08:43 - 08:44  (00:00)    
root     tty1                          Fri Nov 16 08:43 - 08:43  (00:00)    
root     tty1                          Fri Nov 16 08:42 - 08:43  (00:00)    
root     tty1                          Fri Nov 16 08:42 - 08:42  (00:00)    

wtmp begins Fri Nov 16 08:42:48 2007
fsanz@fuckup: ~ $ ps -fea|grep tty1|grep -v grep
root      3526     1  0 Nov16 tty1     00:00:00 /sbin/getty 38400 tty1
fsanz@fuckup: ~ $ ps -fea|grep tty1|grep -v grep
root      3526     1  0 Nov16 tty1     00:00:00 /sbin/getty 38400 tty1
fsanz@fuckup: ~ $ ps -fea|grep tty2|grep -v grep 
root      2512     1  0 Nov16 tty2     00:00:00 /sbin/getty 38400 tty2
```


I've tried cleaning up both /var/run/utmp and /var/log/wtmp, but the ghost users are determined to stay, and they reappear,  *cat exorcismus.au>/dev/null* neither works.


Thanks in advance!

---

### Post by nish.des on 2008-01-30
I run Ubuntu on my home machine and SuSE 9.0 with kernel 2.4.21-99 on an (oldish) office machine.

The SuSE machine gave me a 'gone - no logout' today. Moreover, not on a tty. 
```

nishita  pts/3        ipc41  Wed Jan 30 23:34   still logged in
nishita  pts/6                  Wed Jan 30 13:53    gone - no logout        <<
nishita  pts/5        ff15     Wed Jan 30 13:42 - 13:56 (00:14)
nishita  pts/0                  Tue Jan 22 09:30 - 23:40 (8+14:10)
```

There's the same mystery entry with "gone - no logout." As far as I can remember, nothing extra-ordinary happened today. This is an office machine, so I don't even have root access.

Since this has happened on a completely different machine, perhaps, it is a problem not specific to a particular distribution?

Some googling tells me this has been attributed to a bug in:
1. openSSH (in 2004) [[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=243880]](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=243880]) This has been fixed.
2. reiserfs and later to ntpdate (in 2003) [[http://archive.cert.uni-stuttgart.de/suse-security/2003/02/msg00019.html]](http://archive.cert.uni-stuttgart.de/suse-security/2003/02/msg00019.html])

But both of these bugs are way too old to remain unfixed. Can anyone help?

Regards,
Nishita

---

