---
title: "&quot;Modem monitor&quot; problems"
date: 2005-04-18
forum: General Help
---

### Post by renoir98 on 2005-04-18
I've recently upgraded to hoary from warty and i've found that my good-old "modem lights"
applet has been replaced by a "modem monitor" applet which should handle my dial-up connection.
I'm posting here since i can't have it working,of course.
First:i MUST be root to configure and run it and this is not the best option.
Second:it simply doesn't work and this is the output of the
tail --lines=20 /var/log/messages    command
```
 
Apr 18 15:39:54 localhost pppd[18149]: pppd 2.4.2 started by root, uid 0
Apr 18 15:39:55 localhost pppd[18149]: Serial connection established.
Apr 18 15:39:55 localhost pppd[18149]: Using interface ppp0
Apr 18 15:39:55 localhost pppd[18149]: Connect: ppp0 <--> /dev/ttyS1
Apr 18 15:39:59 localhost pppd[18149]: Serial line is looped back.
Apr 18 15:39:59 localhost pppd[18149]: Connection terminated.
Apr 18 15:39:59 localhost pppd[18149]: Terminating on signal 15.
Apr 18 15:39:59 localhost pppd[18149]: Exit.

```

My external 56k modem is correctly installed since it works fine
with "pon" command from console.

What does "Serial line is looped back" mean?
What may cause this problem?
Is it possible to run the "modem monitor" as a simple user (not root)?
Thanks in advance,renoir.

---

### Post by Nexxus6 on 2005-04-18
I second your problem.  When you do get it work you will get 1/10 of normal speed.  No love for the dialup hoary users.  See here and scroll down to decription: [http://bugzilla.ubuntu.com/show_bug.cgi?id=8890](http://bugzilla.ubuntu.com/show_bug.cgi?id=8890)

---

### Post by renoir98 on 2005-04-18
[QUOTE=Nexxus6]I second your problem.  When you do get it work you will get 1/10 of normal speed.  No love for the dialup hoary users.  See here and scroll down to decription: [http://bugzilla.ubuntu.com/show_bug.cgi?id=8890](http://bugzilla.ubuntu.com/show_bug.cgi?id=8890)[/QUOTE]
 I hope this will be fixex soon.
I need it.

---

